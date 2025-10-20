## Error Codes

| Code | Message | Description |
|------|---------|-------------|
| 1000 | Unrecognized error | |
| 1001 | Timeout | Request timeout |
| 1002 | Param format fail | Request parameter format error |
| 1003 | Session not found! | Session not found |
| 1004 | Function Disabled | Disabled function |
| 1005 | The user has not logged in yet! | Not logged in yet |
| 1006 | Parameter format error | Request parameter format error |
| 1007 | The data is too long to exceed 1024 | Data too long, exceeds 1024 |
| 1008 | Error parsing encrypted file! | Error parsing encrypted file |
| 1009 | Session lost! | Session lost |
| 1010 | Decrypt error! | Decryption error |
| 1011 | Find account addr error! | Account address find error |
| 1012 | The trust has not been registered | Trust has not been registered |
| 1013 | Find Rec Fail! | Record find failed |
| 1014 | Rec count is 0 | Record count is 0 |
| 1015 | Json parse error | JSON parse error |

------------------------------------------------------------------------------------------

## Notes

- The VoidChain platform token can retain up to 9 decimal places, so when transferring and managing tokens, you need to add 9 zeros at the end.
- The platform gives each account about 10 free gas fees per day, but this is not automatic. Each account needs to actively execute a daily free energy retrieval once.
- When operating on the platform, each gas fee will be deducted from the gifted pool first. If exhausted, it will automatically purchase one platform coin's worth of gas energy. The current pricing is also about 10 operations. Purchased gas energy will remain valid and will not be cleared to zero, but the gifted energy will be automatically cleared to zero the next day.
