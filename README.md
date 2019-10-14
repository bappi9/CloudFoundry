# CloudFoundry
Cloud Foundry

Cloud Foundry Login:
cf  login -a api.run.pivotal.io
Email: test@gmail.com
password:test
CF Target Space Change
cf  target -s space name
Push command
cf push space name
React Application Manifest
---
applications:
- name: my-app
  path: build/
  memory: 128M
  instances: 1
  buildpack: https://github.com/cloudfoundry/staticfile-buildpack
React Application CF Publish Process.
At first build your project and ensure create a build folder in your project because of build file transfer to cloud foundry. 
npm build command:  react-scripts build
Create manifest yml file in your project root directory.
Push command: cf push webapplication(SpaceName)

      06. Dot Net Core Application CF Publish Process.
Add dependency nuget package 
Pivotal.Extensions.Configuration.ConfigServerCore
Pivotal.Extensions.Configuration.CloudFoundryCore
Startup cs add dependency in configure service
 // Optional: Adds ConfigServerClientOptions to service container
            services.ConfigureConfigServerClientOptions(Configuration);

            // Optional:  Adds IConfiguration and IConfigurationRoot to service container
            services.AddConfiguration(Configuration);

            // Optional:  Adds CloudFoundryApplicationOptions and CloudFoundryServicesOptions to service container
            services.ConfigureCloudFoundryOptions(Configuration);
Add manifest yml file root directory.
---
applications:
- name: WebApplication
  disk_quota: 20M
  buildpack: https://github.com/cloudfoundry/dotnet-core-buildpack
  services:
    - config-server
Release your project and cmd root directory set publish directory
Project cf push from release folder.

