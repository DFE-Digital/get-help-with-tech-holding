# Get Help With Tech Holding

A holding page for Get Help With Tech

## GOV.UK PaaS

To perform any actions on PaaS the user needs to be "assigned" to the **space** `get-help-with-tech-prod`. Access can be requested on the DfE Slack channel `#govuk-paas`. Further context can be found [here](https://docs.cloud.service.gov.uk/).

### Deployment

To test:

```bash
cf target -s get-help-with-tech-prod
cf push get-help-with-tech-holding-test -b https://github.com/cloudfoundry/nginx-buildpack.git 
```

To update the production site:

```bash
cf target -s get-help-with-tech-prod
cf push get-help-with-tech-holding -b https://github.com/cloudfoundry/nginx-buildpack.git 
```

### Destruction



Test:

```bash
cf target -s get-help-with-tech-prod
cf delete get-help-with-tech-holding-test -f -r
cf delete-route london.cloudapps.digital --hostname get-help-with-tech-holding-test -f
```

Prod:

```bash
cf target -s get-help-with-tech-prod
cf delete get-help-with-tech-holding -f -r
cf delete-route education.gov.uk --hostname get-help-with-tech -f
cf delete-route london.cloudapps.digital --hostname get-help-with-tech-holding -f
cf delete-service get-help-with-tech-prod-cdn-route -f
```
