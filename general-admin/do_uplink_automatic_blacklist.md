# DO\_UPLINK\_AUTOMATIC\_BLACKLIST

A [java regex](https://docs.oracle.com/javase/7/docs/api/java/util/regex/Pattern.html) that precises the uplinks that are allowed when ran **thru an IFT**, once  [DO\_UPLINK](do\_uplink.md) is `true`. If not set, nothing is blacklisted. The regex is evaluated against the ID of the layout

|                      |                                                            |
| -------------------- | ---------------------------------------------------------- |
| `.*`                 | blacklists everything                                      |
| `1128132\|7898132`   | authorizes only the layouts which ID is 1128132 or 7898132 |
| `!1128132\|!7898132` | authorizes all the  layouts except 1128132 or 7898132      |

