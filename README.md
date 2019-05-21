# Osgi Configuration API

This is a rest API to access Apache Sling web console osgi configuration in AEM.

  - Allow to access all configurations
  - filter configuration based on pid
  - filter configuration based on factory pid

# Uses
### All Configuration
  URL - http://host:port/bin/api/osgi-config.json
  
### Filtered Configuration
URL - http://host:port/bin/api/osgi-config.json

***Parameters*** 
- **type** - `pid` or `fid`
- **q** - pid or factory pid 
#### Example
- http://localhost:4504/bin/api/osgi-config.json?type=pid&q=org.apache.sling.security.impl.ReferrerFilter
- http://localhost:4504/bin/api/osgi-config.json?type=fid&q=org.apache.sling.commons.log.LogManager.factory.config

### Json output
It contains array of config objects
```js
{
    "pid": "org.apache.sling.security.impl.ReferrerFilter",
    "changeCount": 1,
    "properties": {
      "filter.methods": [
        "PUT",
        "DELETE"
      ],
      "exclude.agents.regexp": [
        ""
      ],
      "allow.hosts": [
        ""
      ],
      "allow.hosts.regexp": [
        ""
      ],
      "allow.empty": true
    }
  }
```

Factory configuration
``` js
{
    "pid": "org.apache.sling.commons.log.LogManager.factory.config.ef61ce8d-cf4f-410b-9eb5-b1d629161880",
    "fid": "org.apache.sling.commons.log.LogManager.factory.config",
    "bundleLocation": "slinginstall:<AEM-Intallation-DIR>\crx-quickstart\launchpad\startup\1\org.apache.sling.commons.log-5.1.0.jar",
    "changeCount": 1,
    "properties": {
      "org.apache.sling.commons.log.names": [
        "org.apache.sling.scripting.sightly.js.impl.jsapi.ProxyAsyncScriptableFactory"
      ],
      "org.apache.sling.commons.log.level": "ERROR",
      "org.apache.sling.commons.log.pattern": "{0,date,dd.MM.yyyy HH:mm:ss.SSS} *{4}* [{2}] {3} {5}",
      "org.apache.sling.commons.log.file": "logs/error.log"
    }
  }
```

# POM Gson dependency
````xml
<dependency>
	<groupId>com.google.code.gson</groupId>
	<artifactId>gson</artifactId>
	<version>2.8.5</version>
</dependency>
````
