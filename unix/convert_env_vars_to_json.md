# Convert env variables to json

I was migrating a microservice from heroku to aws and needed to take a list of env variables, convert them into json format, and add them to aws secrets manager.

```bash
printenv > env_vars.txt
cat env_vars.txt | jo -p > aws_secrets_manager.json
```

After the json file is created, replace any occurences of `null` with `""` or the json payload cannot be parsed into individual secret values in aws.
