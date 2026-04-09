# Import pandas for data manipulation
import pandas as pd

# Import Dash framework
import dash

# Import HTML components for layout
from dash import html

# Import core Dash components like graphs and sliders
from dash import dcc

# Import callback utilities for interactivity
from dash.dependencies import Input, Output

# Import Plotly Express for charts
import plotly.express as px


# Load the SpaceX dataset into a DataFrame
spacex_df = pd.read_csv("spacex_launch_dash.csv")

# Get maximum and minimum payload values for slider range
max_payload = spacex_df['Payload Mass (kg)'].max()
min_payload = spacex_df['Payload Mass (kg)'].min()


# Initialize the Dash application
app = dash.Dash(__name__)


# Define the layout of the dashboard
app.layout = html.Div(children=[
    html.H1(
        'SpaceX Launch Records Dashboard',
        style={'textAlign': 'center', 'color': '#503D36', 'font-size': 40}
    ),

    dcc.Dropdown(
        id='site-dropdown',
        options=[
            {'label': 'All Sites', 'value': 'ALL'},
            {'label': 'CCAFS LC-40', 'value': 'CCAFS LC-40'},
            {'label': 'CCAFS SLC-40', 'value': 'CCAFS SLC-40'},
            {'label': 'KSC LC-39A', 'value': 'KSC LC-39A'},
            {'label': 'VAFB SLC-4E', 'value': 'VAFB SLC-4E'}
        ],
        value='ALL',
        placeholder='Select a Launch Site Here',
        searchable=True
    ),

    html.Br(),

    html.Div(dcc.Graph(id='success-pie-chart')),

    html.Br(),

    html.P("Payload range (Kg):"),

    dcc.RangeSlider(
        id='payload-slider',
        min=0,
        max=10000,
        step=1000,
        marks={
            0: '0',
            2500: '2500',
            5000: '5000',
            7500: '7500',
            10000: '10000'
        },
        value=[min_payload, max_payload]
    ),

    html.Div(dcc.Graph(id='success-payload-scatter-chart'))
])


# Callback for pie chart
@app.callback(
    Output('success-pie-chart', 'figure'),
    Input('site-dropdown', 'value')
)
def get_pie_chart(entered_site):
    if entered_site == 'ALL':
        fig = px.pie(
            spacex_df,
            values='class',
            names='Launch Site',
            title='Total Success Launches By Site'
        )
        return fig

    filtered_df = spacex_df[spacex_df['Launch Site'] == entered_site]

    counts = filtered_df['class'].value_counts().reset_index()
    counts.columns = ['class', 'count']

    fig = px.pie(
        counts,
        values='count',
        names='class',
        title=f'Total Success vs Failure for site {entered_site}'
    )
    return fig


# Callback for scatter plot
@app.callback(
    Output('success-payload-scatter-chart', 'figure'),
    [
        Input('site-dropdown', 'value'),
        Input('payload-slider', 'value')
    ]
)
def get_scatter_chart(entered_site, payload_range):
    low, high = payload_range

    filtered_df = spacex_df[
        (spacex_df['Payload Mass (kg)'] >= low) &
        (spacex_df['Payload Mass (kg)'] <= high)
    ]

    if entered_site != 'ALL':
        filtered_df = filtered_df[filtered_df['Launch Site'] == entered_site]

    fig = px.scatter(
        filtered_df,
        x='Payload Mass (kg)',
        y='class',
        color='Booster Version Category',
        title=(
            'Payload Effect on Launch Outcome'
            if entered_site == 'ALL'
            else f'Payload Effect on Launch Outcome for {entered_site}'
        )
    )

    fig.update_layout(
        xaxis_title='Payload (kg)',
        yaxis_title='Launch Outcome'
    )

    return fig


# Run the Dash application
if __name__ == '__main__':
    app.run()