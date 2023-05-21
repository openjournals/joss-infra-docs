# Buffy :: Editorial bot

Buffy is a service providing a bot for helping scientific journals manage submission reviews.

It is a Sinatra application that can be configured via a settings YAML file to define commands to listen to and actions to perform in order to automate common editorial tasks.

## Source code
The source code is available at https://github.com/openjournals/buffy and the configuration used for JOSS is in the `joss` branch.

## Deployment
Buffy is deployed in Heroku and configured to act as the [@editorialbot GitHub user](https://github.com/editorialbot) in the [JOSS reviews](https://github.com/openjournals/joss-reviews/issues).

## Documentation
A complete guide on installation, configuration and available responders can be found here: https://buffy.readthedocs.io/en/joss/

## Configuration
The current settings file for the Buffy instance deployed for JOSS is a YAML file where all commands and responders used by JOSS and availbale in the JOSS reviews are defined and configured: https://github.com/openjournals/buffy/blob/joss/config/settings-production.yml
