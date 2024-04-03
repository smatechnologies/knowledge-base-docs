---
sidebar_label: 'Best Practice for Naming OpCon Objects'
hide_title: 'true'
---

## Best Practice for Naming OpCon Objects

**Purpose of naming convention**

This naming convention is designed to provide you guidelines and best practices about the management of your OpCon environment.

An environment respecting a naming convention with rules is easier to understand and manage for everyone as you can retrieve information efficiently and quickly. On another side, it's also easier for you and for **SMA Support** to analyse an environment structured around a convention rather than an environment without any rules.

Please keep in mind that it's *not mandator*y and that you can design your own convention. The following tips are here to provide you a solid base to start your journey with OpCon, to get idea for your own design or to refresh your environment with a predefined framework.
This article will also give you which characters it is **not recommended** to use.

**Advantages**

* Environment is easier to maintain and manage
* It's easier to search for something
* Troubleshooting is more efficient
* Anyone can interact with OpCon environment easily

**General recommendations** 

Avoid the use of special characters in names :
* `( )` Parenthesis
* `;` `,` `.` `!` Punctuation marks
* ` Apostrophe
* `^` Accents
* `Space`
* `?` and `*` are used as wild cards

Avoid using the underscore "`_`" in the name of schedules and jobs because the underscore is used as a separator mark for: 

* Groups of machines
* Multi-instance schedules
* Multi-instance jobs

**Schedules**

* You can standardize the name of your schedules by:

* Type: Schedule SC-, Sub Schedule SS-
* Environment: Production PR-, Test TST-, ...
* Service: Marketing MKT-, Stock STK-, Laboratory LAB-, Finance, FIN-, ...
* Priority: 1 hour 1H-, 1 day 1D-, ...

**Jobs**

You can apply the same rules as for schedules:

* Machine type: UNIX-, WIN-, ...
* RunAgain: UniqueExecution UNQ-, Recurrent job REC-, ...
* Service: Marketing MKT-, Stock STK-, Laboratory LAB-, Finance, FIN-, ...
* Tasks: Shell SH-, Batch BAT-, Python PY-, SQL query SQL-, ...

**Specific rules for IBM i jobs**

* Names must be 10 characters or less.
* If a specific name validation lists a different number of maximum characters, the specific rules override this rule.
* Names must begin with an alphabetic character (A through Z, @, $, and #).
* All subsequent characters can be alphanumeric (A through Z, 0 through 9, @, $, #, and _ (underscore)).
* There can be no embedded blanks.

**Machines**

Machine names in UPPER CASE with a *maximum* of 20 characters.
For **WINDOWS** or **LINUX** machines, the name matches the network name of the machine.
It can be different but you will have to define in the machine configuration an IP or the FQDN.
For **SQL** machines, indicate the network name of the machine + "**-SQL**" and complete the fully qualified domain name:
PTRXORD01-SQL (with the domain name mydomain.local)

Use of groups of machines to run processes on a set of machines: 

* 20 characters maximum.
* Prefixed by 3/4 letters corresponding to the type (WIN or UNIX) + dash "-" + n letters corresponding to the application:
    * IBM-BACKUP
    * WIN-PURGE
    * UNIX PURGE
    * WIN-BACKUP

**Properties**

Managed System Properties start with the character $, the OpCon date variable and the custom name (specify format):
For both `$SCHEDULE DATE` and `$DATE` we can create a new property with a new name, the purpose is to get a different format than the original one.

`$SCHEDULE DATE ddmmyyyy`

`$DATE yymm` 

User Global Properties contain only the name (*without `$`*), you can also use a prefix for your property name like :

* Path-
* Schedule-
* Job-
* Login-
* Password-

**Resources/Thresholds**

* A *maximum* of 20 characters
* Prefix: R-
* Then name the Resource in CamelCase

In the documentation field, you can specify:

* The maximum value of the Resource 
* The context of use of this Resource

T-ThresholdName:

* A maximum of 20 characters
* Prefix: T-
* Then name the Threshold in CamelCase

In the documentation field, you can specify:

* The initial value of the Threshold 
* The context of use of this Threshold

**Tags**

Tag name in CamelCase.

**To go further...**

Don't forget to document your schedules, jobs, properties, etc. to help other users understand what it the purpose of everything and if they need to take particular precautions while working on a specific item.