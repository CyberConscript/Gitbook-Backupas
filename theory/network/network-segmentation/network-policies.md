# Network policies

An ACL is used as a loose standard to create a ruleset for different implementations and access control protocols. In this task, we will use ACLs within a router to decide whether to route or drop a packet based on the defined list.

An ACL contains **ACE(s)** (**A**ccess **C**ontrol **E**ntry) or rules that define a list’s profile based on pre-defined criteria (source address, destination address, etc.)

how VyOS creates an ACL and defines the policy.

Create the new access-list policy, defining the ACL number (1 - 2699)

`set policy access-list <acl_number>`

Set the description of the access list.

`set policy access-list <acl_number> description <text>`

Create a new rule (or ACE) under the ACL and define the action of the rule.

`set policy access-list <acl_number> rule <1-65535> action <permit|deny>`

Define criteria or parameters for the rule to enforce/match.

`set policy access-list <acl_number> rule <1-65535> <destination|source> <any|host|inverse-mask|network>`





