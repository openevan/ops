# LACP commands

## Contents

- [LACP configuration commands](#lacp-configuration-commands)
	- [Global context commands](#global-context-commands)
		- [Creation of LAG interface](#creation-of-lag-interface)
		- [Deletion of LAG interface](#deletion-of-lag-interface)
		- [Configuring LACP system priority](#configuring-lacp-system-priority)
		- [Configuring default LACP system priority](#configuring-default-lacp-system-priority)
	- [Interface context commands](#interface-context-commands)
		- [Assigning interface to LAG](#assigning-interface-to-lag)
		- [Removing interface from LAG](#removing-interface-from-lag)
		- [Configuring LACP port-id](#configuring-lacp-port-id)
		- [Configuring LACP port-priority](#configuring-lacp-port-priority)
	- [LAG context commands](#lag-context-commands)
		- [Entering into LAG context](#entering-into-lag-context)
		- [Configuring LACP mode](#configuring-lacp-mode)
		- [Configuring hash type](#configuring-hash-type)
		- [Configuring LACP fallback mode](#configuring-lacp-fallback-mode)
		- [Configuring LACP rate](#configuring-lacp-rate)
- [LAG display commands](#lag-display-commands)
	- [Display global LACP configuration](#display-global-lacp-configuration)
	- [Display LACP aggregates](#display-lacp-aggregates)
	- [Display LACP interface configuration](#display-lacp-interface-configuration)

## LACP configuration commands
### Global context commands
#### Creation of LAG interface
##### Syntax

```
    interface lag ID
```

##### Description
This command creates a LAG interface represented by an ID.

##### Authority
all users

##### Parameters
This command takes an ID as a parameter which represents a LAG interface. The LAG interface ID can be in the range of 1 to 2000.

##### Examples

```
switch(config)# interface lag 100

switch(config-lag-if)#
```

#### Deletion of LAG interface
##### Syntax

```
 no interface lag ID
```

##### Description
This command deletes a LAG interface represented by an ID.

##### Authority
all users

##### Parameters
This command takes an ID as a parameter which represents a LAG interface. The LAG interface ID can be in the range of 1 to 2000.

##### Examples

```
switch(config)# no interface lag 100
```

#### Configuring LACP system priority
##### Syntax

```
    lacp system-priority <0-65535>
```

##### Description
This command sets an LACP system priority.

##### Authority
all users

##### Parameters
This command takes a system priority value in the of range 0 to 65535.

##### Examples

```
switch(config)# lacp system-priority 100
```

#### Configuring default LACP system priority
##### Syntax

```
    no lacp system-priority
```

##### Description
This command sets an LACP system priority to a default(65534).

##### Authority
all users

##### Parameters
no parameters

##### Examples

```
switch(config)# lacp system-priority 100
```

### Interface context commands
#### Assigning interface to LAG
##### Syntax

```
    lag ID
```

##### Description
This command adds an interface to a LAG interface specified by an ID.

##### Authority
all users

##### Parameters
This command takes an ID as a parameter which represents a LAG interface. The LAG interface ID can be in the range of 1 to 2000.

##### Examples

```
switch(config)# interface 1
switch(config-if)# lag 100
```

#### Removing interface from LAG
##### Syntax

```
    no lag ID
```

##### Description
This command removes an interface from a LAG interface specified by an ID.

##### Authority
all users

##### Parameters
This command takes an ID as a parameter which represents a LAG interface. The LAG interface ID can be in the range of 1 to 2000.

##### Examples

```
switch(config)# interface 1
switch(config-if)# no lag 100
```

#### Configuring LACP port-id
##### Syntax

```
    lacp port-id <1-65535>
```

##### Description
This command sets an LACP port-id value of the interface.

##### Authority
all users

##### Parameters
This command takes a port-id value in the range of 1 to 65535.

##### Examples

```
switch(config-if)# lacp port-id 10
```

#### Configuring LACP port-priority
##### Syntax

```
    lacp port-priority <1-65535>
```

##### Description
This command sets an LACP port-priority value for the interface.

##### Authority
all users

##### Parameters
This command takes a port-priority value in the range of 1 to 65535.

##### Examples

```
switch(config-if)# lacp port-priority 10
```

### LAG context commands
#### Entering into LAG context
##### Syntax

```
    interface lag ID
```

##### Description
This command enters into the LAG context of the specified LAG ID. If the specified LAG interface is not present, this command creates a LAG interface and enters it into the LAG context.

##### Authority
all users

##### Parameters
This command takes an ID as a parameter which represents a LAG interface. The LAG interface ID can be in the range of 1 to 2000.

##### Examples

```
switch(config)# interface 1
switch(config-if)# lag 100
```

#### Configuring LACP mode
##### Syntax

```
    [no] lacp mode {active/passive}
```

##### Description
This command sets an LACP mode to active or passive.
The **no** form of the command sets the LACP mode to **off**.

##### Authority
all users

##### Parameters
This command takes an **active** or **passive** keyword as an argument to set an LACP mode.

##### Examples

```
switch(config)# interface lag 1
switch(config-lag-if)# lacp mode active
switch(config-lag-if)# no lacp mode active
```

#### Configuring hash type
##### Syntax
    hash l2-src-dst

##### Description
This command sets an LACP hash type to l2-src-dst. The default is l3-src-dst.
The **no** form of the command sets an LACP hash type to l3-src-dst.

##### Authority
all users

##### Parameters
no parameters.

##### Examples

```
switch(config)# interface lag 1
switch(config-lag-if)# hash l2-src-dst
switch(config-lag-if)# no hash l2-src-dst
```

#### Configuring LACP fallback mode
##### Syntax

```
    lacp fallback
```

##### Description
This command enables an LACP fallback mode.
The **no** form of the command disables the an LACP fallback mode.

##### Authority
all users

##### Parameters
no parameters.

##### Examples

```
switch(config)# interface lag 1
switch(config-lag-if)# lacp fallback
switch(config-lag-if)# no lacp fallback
```

##### Configuring LACP rate
##### Syntax

```
    lacp rate fast
```

##### Description
This command sets an LACP heartbeat request time to **fast**. The default is **slow**, which is once every 30 seconds. The **no** form of the command sets an LACP rate to **slow**.

##### Authority
all users

##### Parameters
no parameters.

##### Examples

```
switch(config)# interface lag 1
switch(config-lag-if)# lacp rate fast
```

## LAG display commands
### Display global LACP configuration
#### Syntax

```
    show lacp configuration
```

#### Description
This command displays global a LACP configuration.

#### Authority
all users

#### Parameters
no parameters

#### Examples

```
switch# show lacp configuration
System-id       : 70:72:cf:ef:fc:d9
System-priority : 65534
```

### Display LACP aggregates
#### Syntax

```
    show lacp aggregates [lag-name]
```

#### Description
This command displays all LACP aggregate information if no parameter is passed. If a LAG name is passed as an argument, it shows information of the specified LAG

#### Authority
all users

#### Parameters
This command takes a LAG name as an optional parameter.

#### Examples

```
switch# show lacp aggregates lag100
Aggregate-name          : lag100
Aggregated-interfaces
Heartbeat rate              : slow
Fallback                        : false
Hash                             : l3-src-dst
Aggregate mode           : off

switch# show lacp aggregates
Aggregate-name          : lag100
Aggregated-interfaces
Heartbeat rate             : slow
Fallback                       : false
Hash                            : l3-src-dst
Aggregate mode         : off

Aggregate-name        : lag200
Aggregated-interfaces
Heartbeat rate             : slow
Fallback                       : false
Hash                             : l3-src-dst
Aggregate mode           : off
```

### Display LACP interface configuration
#### Syntax

```
    show lacp interfaces [IFNAME]
```

#### Description
This command displays an LACP configuration of the physical interfaces. If an interface name is passed as argument, it only displays an LACP configuration of a specified interface.

#### Authority
all users

#### Parameters
This command takes an interface name as an optional parameter.

#### Examples

```
switch# show lacp interfaces
State abbreviations
A - Active        P - Passive      F - Aggregable I - Individual
S - Short-timeout L - Long-timeout N - InSync     O - OutofSync
C - Collecting    D - Distributing
X - State m/c expired              E - Default neighbor state
.
Actor details of all interfaces
\-------------------------------------------
Intf-name    Key    Priority   State
\-------------------------------------------
Aggregate-name : lag100
1                            500
Aggregate-name : lag200
3
4
2
.
Partner details of all interfaces
\-------------------------------------------------
Intf-name    Partner  Key    Priority   State
                     port-id
\-------------------------------------------------
Aggregate-name : lag100
1                      500
Aggregate-name : lag200
3
4
2
```