# Environement for the frontend

* node5.1
* phantomjs 2.0

## Installation

    docker build . talkspirit/frontend
    docker tag talkspirit/frontend talkspirit/frontend:5.1
    docker push talkspirit/frontend::5.1
