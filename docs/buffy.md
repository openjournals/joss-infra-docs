# Buffy

Buffy is a service to provide a bot helping scientific journals manage submission reviews.
It is a Sinatra application that can be configured via a settings YAML file to define commands to listen to and actions to perform in order to automate common editorial tasks.
The source code is available at https://github.com/openjournals/buffy and the configuration used for JOSS is in the `joss` branch.

Buffy is deployed in Heroku and configured to act as the @editorialbot GitHub user in the JOSS reviews.

A complete guide on installation, configuration and available responders can be found here: https://buffy.readthedocs.io/en/joss/

This is a link to the current configuration file for the JOSS deployment, tt's a YAML file where all commands and responders used by JOSS and availbale in the JOSS reviews are configured: https://github.com/openjournals/buffy/blob/joss/config/settings-production.yml
