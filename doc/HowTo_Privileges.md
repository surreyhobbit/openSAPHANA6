# Privileges for Container Access

The module / resource definition in a container contains the name of the 
Schema and the container manages access via its own technical user.

One container can give access to other (cross-container access) by entering
another container (or schema?) into the resource (or module?) definition.

In that case a arget container needs to be entered (that is the one that all artefacts will
be deployed to).

# Structured Privileges (similar to analytical privilege)
these are needed if you want to grant access to a container e.g. for external r
reporting tools

Need to create a DB role for that, allows instance filtering on CDS views

There is a special role with a specific name that is granted automatically to 
the technical container pplication user:

`default_access_role.hbrole`

It is *important* that this role is created in the `src/default` folder

# Cross container access

Launch the SAP HANA XS Advanced Cockpit:

[link](https://ec2-34-231-45-95.compute-1.amazonaws.com:51041)

If port is unknown, logon with `xs-admin-login` and list all apps with `xs apps`
then find the cockpit web app in the list

# User Provided Service using command line
(p47)
If XSA Cockpit not working then use CLI:

```
xs cups CROSS_SCHEMA_SFLIGHT_00 -p "{\"host\":\"ec2-34-231-45-95.compute-1.amazonaws.com\",\"port\":\"39013\",\"user\":\"SYSTEM\",\"password\":\"<passw0rd>\",\"driver\":\"com.sap.db.jdbc.Driver\",\"tags\":[\"hana\"] , \"schema\" : \"SFLIGHT\" }"
```

which gives response

see also this link [link](https://github.com/SAPDocuments/Tutorials/blob/master/tutorials/xsa-create-user-provided-anonymous-service/xsa-create-user-provided-anonymous-service.md)

```json
{
  "name" : "CROSS_SCHEMA_SFLIGHT_00",
  "credentials" : {
    "schema" : "SFLIGHT",
    "password" : "PasswrdBl00na",
    "driver" : "com.sap.db.jdbc.Driver",
    "port" : "39013",
    "host" : "ec2-34-231-45-95.compute-1.amazonaws.com",
    "user" : "SYSTEM",
    "tags" : [ "hana" ]
  }
}
```
### Error handling

When having problems with the user provided service, try to update the port to 3<instance>15 for MDC and also try a different host (check the XSADMIN console what other service are using for the host).
  
  You can use the following command line for updating the ups in interactive mode with parameters :
  
  `xs uups -p "host, port"`
  
  see also (https://docs.cloudfoundry.org/devguide/services/user-provided.html)
  
  ALso change the user for the service to the XSA_DEV user instead of the system user:
  https://answers.sap.com/questions/274657/sap-web-ide-for-sap-hana-build-error-more-than-one.html
  

### Issue resolution
Problem was that services were created in the wrong space (SAP instead of development).
To fix this, log off from xs admin in CLI, and re-log-on like this:
`xs login -s development`
That logs you in in the new space
There, check `xs service` and you'll see that the service isn't there.

The create the service there as above or with the interactive mode (using cloud foundry command cuups):

```
xs cups CROSS_SCHEMA_SFLIGHT_00 -p "host, port, user, password, driver, tags, schema"
```

and use the inputs as per above.

```
    "schema" : "SFLIGHT",
    "password" : "PasswrdBl00na",
    "driver" : "com.sap.db.jdbc.Driver",
    "port" : "39013",
    "host" : "ec2-34-231-45-95.compute-1.amazonaws.com",
    "user" : "SYSTEM",
    "tags" : [ "hana" ]
```


### Granting access to the container users
Create a file in the *cfg* folder, e.g. `SFLIGHT.hdbgrants`

enter something like:

```json
{
"hdi-sflight-service": {
"object_owner" : { "schema_privileges":[
{
"privileges_with_grant_option":["SELECT", "SELECT METADATA"]
} ]
},
"application_user" : {
"schema_privileges":[ {
"reference":"SFLIGHT",
"privileges_with_grant_option":["SELECT", "SELECT METADATA"]
} ]
} }
}
```

This is assigning access to the SFLIGHT schema to both the container technical users – owner and application user. 
The grant is performed by the user provided service and the database user you configured in that user provided service.
(so in the service the user needs to be a DB user).

(https://github.com/SAP/com.sa p.openSAP .hana5.templates/bl ob/hana2_sps02/ex2/ex2_12)

Then synonyms need to be created in this way:

```json
{
  "SFLIGHT": {
    "target": {
      "object": "SFLIGHT",
      "schema": "SFLIGHT"
    }
  },
  "SBOOK": {
    "target": {
      "object": "SBOOK",
      "schema": "SFLIGHT"
    }
  },
  "SPFLI": {
    "target": {
      "object": "SPFLI",
      "schema": "SFLIGHT"
    }
  }
} 
```