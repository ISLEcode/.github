### Overview

>   The community benefits of GitHub are substantial, but they also carry potential risks. The fact that anyone can propose bug
>   fixes publicly comes with certain responsibilities. The most important is the responsible disclosure of information that
>   could lead to security exploits before their underlying bugs can be fixed. Developers looking to report or address security
>   issues look for a `SECURITY.md` file in the root of a repository in order to responsibly disclose their concerns. Providing
>   guidance in this file will ultimately speed up the resolution of these critical issues.

Building and deploying secure software component and applications involves many aspects; in all cases the following three
considerations should always be weighed:

-   **I know that I know nothing about SECURITY**\
    Cybersecurity is a constantly evolving discipline; adopt the [Socratic paradox][socratic-paradox].

-   **Keep it simple, SECURE**\
    Revisited [KISS principle][kiss-principle] that insuflates security as a primary concernt from day zero.

-   **SECURED day-to-day delivery processes**\
    Recurring security testing through [DevOps] workflows enforcing the organisations' rules and regulations.

  [socratic-paradox]:   https://en.wikipedia.org/wiki/I_know_that_I_know_nothing
  [kiss-principle]:     https://en.wikipedia.org/wiki/KISS_principle
  [devops]:             https://en.wikipedia.org/wiki/DevOps

### GitHub best practices

1.  **Don't keep ANY sensitive files in a repository**

    _Sensitive files_ are not always easily detectable, these could be – and often are, benign intermediate build files typically
    used for testing purposes and which contain, for instance, API keys or private configuration data.

    > It should be assumed that any data committed to GitHub at any point has been compromised.

    a)  Before the event security is commonly achieved through:

        -   Exhaustive enumeration of files which SHOULD NEVER be commited in [.gitignore][] files. These files instruct client
            tools, such as the `git` command line utility, to [ignore paths and patterns][.gitignore-eg] when aggregating files
            for a commit. Though multiple such files can be created in a same Git repository; we recommend concentrating all rules
            in a single file in the top level directory.

        -   Always clean up your sandbox environment before commiting changes. For instance, when using the GNU Autotools build
            toolchain, perform a `make distclean` – and not `make clean` or `make realclean`, before any commit.

        -   The `.gitignore` method is not bullet proof. Repository maintainers should

    b)  After the event security occurs when sensitive information has been commited. The Git database needs to be cleanup to
        remove all traces of that information; simply overwriting a commit isn't enough to ensure the data will not be accessible
        in the future. See GitHub's instructions on [removing sensitive data from a repository][zap-git-db].

  [.gitignore]:     https://help.github.com/github/using-git/ignoring-files
  [.gitignore-eg]:  https://github.com/github/gitignore
  [zap-git-db]:     https://help.github.com/github/authenticating-to-github/removing-sensitive-data-from-a-repository


