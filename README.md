# Surreal 
Backend code for the NASA Space Apps 2022 competition. Created by Space Jam.

Space Jam consists of the following members (listed in alphabetical order):
- Akim Niyo
- Dimitri Senevitratne 
- Fernando Rubio Garcia 
- Grant Johnson
- Greg Heiman
- Murphy Ownbey

The challenge: Take Flight: Making the Most of NASA’s Airborne Data

Surreal combines NASA airbourne data with Census Bureau economic data to provide
dynamic visualizations in an easy to use mobile interface (housed in a different repository).

# Dependencies
- Python 3.10
- Pipenv

# How to Run
This project uses Pipenv for dependency management. 

1. Install Pipenv
```
pip install --user pipenv
```

2. Begin Pipenv shell
```
pipenv shell
```

3. Install project's dependencies
```
pipenv install
```

4. Run the project (Gunicorn only works on Linux/Unix systems)
```
gunicorn -c gunicorn.conf.py -b :5000 main:app
```

# Public API
This API is currently hosted publicly using Google Cloud. If you would like to hit this endpoint without needing
to install or build the project you can access the API at the following URL:

`https://space-app-364302.uc.r.appspot.com/api/v1/google-cloud-service/filename/2020_pcp.png`

The data will be returned in the following format:
```
{
    "filename": "..."
    "callback_url": "...",
}
```

The `callback_url` field is a signed URL from Google Cloud that is valid for 1 hour. With this URL you can download and view the visualizations.

You can change the final parameter to a variety of file names in order to see multiple different data sets visualized.

There is also an endpoint to see what the graph data looks like. You can access this endpoint at the following URL:

`https://space-app-364302.uc.r.appspot.com/api/v1/chart-service/chart/1`

This will return a JSON with all of the data needed to plot the graph using Plotly.js.
