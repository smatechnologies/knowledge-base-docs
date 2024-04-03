---
sidebar_label: 'Deploy Transformation Rule UNIX Start Image'
hide_title: 'true'
---

## Deploy Transformation Rule UNIX Start Image

**What is the issue?**

If a **transformation rule** is created to replace/modify the start image of a **UNIX** Job to use a variable starting by a "$" character, you'll encounter an issue at the deployment of the schedule on your target environment as the character is not escaped.

![](../static/img/rtaImage-31.png)

**How to solve it?**

The solution here is to prefix your `$variable` by a **backslash** in order to escape it correctly:

![](../static/img/rtaImage-32.png)

The backslash disappears after deployment:

![](../static/img/rtaImage-33.png)

