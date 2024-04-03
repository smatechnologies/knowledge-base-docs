---
sidebar_label: 'How to Set Specific Permissions On a Received File For File Transfer Job Windows to UNIX'
hide_title: 'true'
---

## How to Set Specific Permissions On a Received File For File Transfer Job Windows to UNIX

**What?**

In this article, we'll see how to set specific permissions on a received file for **File Transfer** job Windows to UNIX.
A file transferred by **SMAFT** from Windows to UNIX usually gets **700** permissions once it is on the destination folder.

**How?**

It is possible to change this default value by editing the **smaft_pps** script located in the **bin** folder of the UNIX LSAM.
On line 62 of the **smaft_pps** script in the agent's bin directory (by default `/usr/local/lsam/bin`), replace:

```
esac
RETVAL=$?
rm -f $FILE > /dev/null 2>&1
touch ../$FILE
fi
```

with:

```
esac
RETVAL=$?
rm -f $FILE > /dev/null 2>&1
chmod 0664 ../$FILE
touch ../$FILE
fi
```


At the line `chmod 0664 ../$FILE` you have to choose the rights for the destination, here in the example it is **644**.

So every transferred files by SMAFT from a Windows machine to this Unix machine will get the permission set to ***644***.