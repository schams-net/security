# Arbitrary Code Execution (TYPO3 Extensions)

## Issue Details

* Creation date: 22 January 2019
* Disclosure date: 04 March 2019
* Status: won't be fixed
* TYPO3 advisory ID: N/A

## Summary

There are a number of publicly available TYPO3 extensions that allow backend users to embed PHP code as content elements from the administration interface directly into a TYPO3 system. Snippets of code that make modifications to TYPO3 get inserted and provide a convenient way to add functionality, but come with a significant drawback.

Arbitrary code execution (ACE) is a high security risk and can lead to unauthorised access, a potential privilege escalation and a fully compromised TYPO3 instance. To exploit this vulnerability, both a valid backend user account and appropriate permissions to use the extensions are required.

In view of the fact that the purpose of these extensions is to execute PHP code and authors explicitly point out this functionality as the main "*feature*", this cannot be classified as a security vulnerability as such. Although this solution is not considered best practise, the logical consequence is that the TYPO3 Security Team tolerates extensions of this type and nature.

## Background

By adding malicious code backend users with limited access permissions can misuse this functionality, which can lead to server-side execution of PHP code, privilege escalation, etc.

It is relevant to bear in mind that the below-mentioned extension is merely an example and one of several extensions that provides this (or a similar) functionality. All of them are available in the official TYPO3 Extension Repository (TER) and Git repositories such as GitHub, GitLab and Bitbucket.

It is also important to understand that these extensions are third party products and not an integral part of the TYPO3 core or of any default installation.

The TYPO3 extension "[joppnet] PHP Content Element" (extension key: `jn_phpcontentelement`) [[1](https://extensions.typo3.org/extension/jn_phpcontentelement/)][[2](https://github.com/joppnet/jn_phpcontentelement)] allows backend users to add arbitrary PHP code as content elements. The code is then executed in the frontend of a TYPO3 application.

> "_Extension description: Allows you to add PHP scripts via frontend plugin._" [[1](https://extensions.typo3.org/extension/jn_phpcontentelement/)]

## Demo Exploit

What could possibly go wrong?

See [[3](https://raw.githubusercontent.com/schams-net/security/master/TYPO3/2019/20190304-arbitrary-code-execution-typo3-extensions/demo-800x434.mp4)]

Example code used in the video to exploit the vulnerability: see [[4](https://github.com/schams-net/security/blob/master/TYPO3/2019/20190304-arbitrary-code-execution-typo3-extensions/exploit.php)]

## Recommendation

Users are advised not to install extensions that load and execute PHP code from other sources or that allows editors to add PHP snippets. To safely add functionality that goes beyond TYPO3's core capabilities, create extensions that provide the functionality as needed in a controlled and secured way. If this is not possible, an alternative, temporary workaround is to at least configure the system to only allow backend users with administrator rights to install and/or change the PHP code executed in TYPO3.

It is important to understand that the issue described in this article is **not** a security vulnerability in the TYPO3 core, nor a (hidden) security issue of a TYPO3 extension. TYPO3 administrators are advised to choose the extensions they install in a TYPO3 instance wisely.

## History

**22 January 2019**
* Issue was discovered and documented.
* TYPO3 Security Team was contacted.

**23 January 2019**
* TYPO3 Security Team rejected the issue (ticket `#20190122xxxxxxxxxx`).

**04 March 2019**
* Demo published by [Michael Schams](https://schams.net) [[5](https://github.com/schams-net/security/TYPO3/2019/20190304-arbitrary-code-execution-typo3-extensions/)]

## References

[1] https://extensions.typo3.org/extension/jn_phpcontentelement/  
[2] https://github.com/joppnet/jn_phpcontentelement  
[3] [demo-800x434.mp4](https://raw.githubusercontent.com/schams-net/security/master/TYPO3/2019/20190304-arbitrary-code-execution-typo3-extensions/demo-800x434.mp4)  
[4] [exploit.php](https://github.com/schams-net/security/blob/master/TYPO3/2019/20190304-arbitrary-code-execution-typo3-extensions/exploit.php)  
[5] [GitHub](https://github.com/schams-net/security/TYPO3/2019/20190304-arbitrary-code-execution-typo3-extensions/)  
