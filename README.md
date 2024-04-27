# ADF Auto 
"*Give your CI/CD pipelines a truer continuous integration experience*" [™](https://techcommunity.microsoft.com/t5/azure-data-factory-blog/automated-publish-improvement-in-adf-s-ci-cd-flow/ba-p/2117350)

## Quick start

1. Create new `adf-<DATA FACTORY NAME>.yml` from `adf-COPY-ME.yml` template under `.devops` and update variables/trigger path.
2. Connect development Data Factory to repo and set root path as `/adf/<DATA FACTORY NAME>`
   * Set branch `main` as the collaboration branch.
   * Setting branch `adf_publish` as the publish branch is only for initialization, but is not used afterwards.
3. Check box to "*Disable publish from ADF studio*".
4. Check box to "*Include global parameters in ARM template*". (optional)
   * Global parameters are formatted as `default_properties_<PARAM_NAME>_value` in pipeline.
5. Add `adf-<DATA FACTORY NAME>.yml` as a pipeline in Azure DevOps.
6. Make any change in the development ADF and click save (publish should be disabled).
7. Validate the pipeline ran and deployed your changes.
8. To identify available data factory parameters, view the `ARMTemplateParametersForFactory.json` pipeline artifact after the build runs.
   * If the data factory parameter needs to be a "SecureString", prefix the parameter with `__secure__`.
9. Require Pull Requests into the main branch so that only feature branches can be saved from the development Data Factory.
   * Pull Requests are required after setting any branch policy.

[Microsoft Doc](https://learn.microsoft.com/en-us/azure/data-factory/continuous-integration-delivery-improvements)