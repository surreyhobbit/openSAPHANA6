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
