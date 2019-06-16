[![Board Status](https://dev.azure.com/anuptiwary47/0467592c-dde3-4026-a47d-817d1d464127/1b5968fc-7975-435b-9b76-75987c88a2ee/_apis/work/boardbadge/a0f8acb0-dbf0-4c93-872c-39599d2055b3)](https://dev.azure.com/anuptiwary47/0467592c-dde3-4026-a47d-817d1d464127/_boards/board/t/1b5968fc-7975-435b-9b76-75987c88a2ee/Microsoft.RequirementCategory)
# .NET Sample App

Push the app with no-start:
```
cf push environment -s windows2012R2 -b hwc_buildpack --no-start -p ./ViewEnvironment/
```

If Diego is enabled by default on your CF deployment, you can omit the `--no-start` flag.

If it's not, or if you're not sure, you'll need to install the [Diego Enabler](https://github.com/cloudfoundry-incubator/diego-enabler) CLI plugin:
```
cf add-plugin-repo CF-Community http://plugins.cloudfoundry.org/
cf install-plugin Diego-Enabler -r CF-Community
```

Enable diego and start your app:
```
cf enable-diego environment
cf start environment
```

If you're having this problem pushing the application:
```
FAILED
Server error, status code: 400, error code: 210003, message: The host is taken: environment
```
try adding ```--random-route``` to the ```cf push``` command:
```
cf push environment -s windows2012R2 -b hwc_buildpack --no-start -p ./ViewEnvironment/ --random-route
```
to avoid the host names clashing.

Once your app is pushed, you can navigate to the app's URL and you will
see all the VCAP variables.  Add ?all= to get all the system variables
too.

After your first push, you can simply push your updates without any additional command line arguments:

```
cf push environment
```
