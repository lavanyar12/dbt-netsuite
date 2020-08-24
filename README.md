Welcome to your new dbt project!

### Using the starter project

# Steps used to create this starter project
$ cd ~/Github
- dbt init dbt_netsuite
- cd dbt_netsuite

# Follow instructions on https://hub.getdbt.com/fivetran/netsuite/latest/

Installation instructions
Include this package in your packages.yml - check our installation guide for installation instructions.

Check the location of your NetSuite data — if it is in a schema named netsuite and in the same database as your target database, no further modification is required. If it is in a different database or schema:

Copy the src_netsuite.yml file into your own project.
Uncomment the schema and the database configurations, updating the values for your own data source.¹
Execute dbt run – the NetSuite models will get built as part of your run!

Execute dbt test — these models include tests to check the output of the models.

Database support
These package can be used on Snowflake, BigQuery, and Redshift.

# Update dbt_project.yml
line 5 -> name: 'dbt_netsuite'
line 10 -> profile: 'default'

# delete or comment lines from line 28 # Configuring models as we are going to be using the models defined in installed package, not our own

# delete models/example folder and models/schema.yml if you used dbt init to create this project

# update profiles.yml
added profile called default
default: # this needs to match the profile: in your dbt_project.yml file
  target: dev
  outputs:
    dev:
      type: bigquery
      method: service-account
      keyfile: # replace this with the full path to your keyfile
      project: # Replace this with your project id on GCP
      dataset: # Replace this with dbt_your_name, e.g. dbt_bob
      threads: 1
      timeout_seconds: 300
      location: US
      priority: interactive

Try running the following commands:
- dbt run
- dbt test

- dbt docs generate
- dbt docs serve 

### Resources:
- Learn more about dbt [in the docs](https://docs.getdbt.com/docs/introduction)
- Check out [Discourse](https://discourse.getdbt.com/) for commonly asked questions and answers
- Join the [chat](http://slack.getdbt.com/) on Slack for live discussions and support
- Find [dbt events](https://events.getdbt.com) near you
- Check out [the blog](https://blog.getdbt.com/) for the latest news on dbt's development and best practices
