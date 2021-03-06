# V9: Resiliency Against Reverse Engineering Requirements

## Control objective

This section covers defense-in-depth measures that are recommended for apps that process, or give access to, sensitive data or functionality. Lack of any of these controls does not cause a vulnerability - instead, they are meant to increase the app's resiliency against reverse engineering, making it more difficult for adversaries to gain an understanding of the app's internals or extract data from the app.

The controls in this section differ from previous sections in that they do not apply to all mobile apps generically. Rather, the controls described here should be applied as needed, based on a risk assessment as per the unauthorized modification and/or reverse engineering of the app.

The OWASP document "Technical Risks of Reverse Engineering and Unauthorized Code Modification Reverse Engineering and Code Modification Prevention" (see references below) lists business risks as well as dependent technical threats related to tampering and reverse engineering. In the sections below, we refer to the technical threats described in that document.

For any of the controls in the list below to be effective, the app must fulfill at least all of MASVS-L1, as well as all lower-numbered requriements in V9.

**Note that software protections must never be used as a replacement for security controls. The controls listed in MASVR-R are intended to add threat-specific, additional protective controls to apps that also fulfill the MASVS security requirements.**

### App Isolation

| # | Description | R |
| --- | --- | --- | --- |
| **9.1** | The app provides a custom keyboard whenever sensitive data is entered. | ✓ |
| **9.2** | Custom UI components are used to display sensitive data. The UI components should not rely on immutable data structures. | ✓ |
### Impede Dynamic Analysis and Tampering

| # | Description | R |
| --- | --- | --- | --- |
| **9.3** | The app implements two or more functionally independent methods of root detection and responds to the presence of a rooted device either by alerting the user or terminating the app. | ✓ |
| **9.4** | The app implements multiple functionally independent debugging defenses that, in context of the overall protection scheme, force adversaries to invest significant manual effort to enable debugging. All available debugging protocols must be covered (e.g. JDWP and native). | ✓ |
| **9.5** | The app detects, and responds to, tampering with executable files and critical data. | ✓ |
| **9.6** | The app detects the presence of widely used reverse engineering tools, such as code injection tools, hooking frameworks and debugging servers. | ✓ |
| **9.7** | The app detects, and response to, being run in an emulator using any method.   | ✓ |
| **9.8** | The app detects, and responds to, modifications of process memory, including relocation table patches and injected code.  | ✓ |
| **9.9** | The app implements multiple different responses to tampering, debugging and emulation (requirements 9.2 - 9.6), including stealthy responses that don't simply terminate the app. | ✓ |
| **9.10** |All executable files and libraries belonging to the app are either encrypted on the file level and/or important code and data segments inside the executables are encrypted or packed. Trivial static analysis should not reveal important code or data. | ✓ |
| **9.11** | Obfuscating transformations and functional defenses are interdependent and well-integrated throughout the app. | ✓ |

### Device Binding

| # | Description | R |
| --- | --- | --- | --- |
| **9.12**| The app implements a 'device binding' functionality when a mobile device is treated as being trusted. Verify that the device fingerprint is derived from multiple device properties.  | ✓ |

### Impede Comprehension

| # | Description | R |
| --- | --- | --- | --- |
| **9.13** | The app uses multiple functionally independent means of emulator detection that, in context of the overall protection scheme, force adversaries to invest significant manual effort to run the app in an emulator (supersedes requirement 9.5). | ✓ 
| **9.14** | If the architecture requires sensitive information be stored on the device, the app only runs on operating system versions and devices that offer hardware-backed key storage. Alternatively, the information is protected using obfuscation. Considering current published research, the obfuscation type and parameters are sufficient to cause significant manual effort to reverse engineers seeking to comprehend or extract the sensitive data. | ✓ |
| **9.15** | If the architecture requires sensitive computations be performed on the client-side, these computations are isolated from the operating system by using a hardware-based SE or TEE. Alternatively, the information is protected using obfuscation. Considering current published research, the obfuscation type and parameters are sufficient to cause significant manual effort to reverse engineers seeking to comprehend the sensitive portions of the code and/or data.  | ✓ |

## References

For more information, see also:

- OWASP Mobile Top 10: M8 - Code Tampering, M9 - Reverse Engineering
- WASP Reverse Engineering Threats -https://www.owasp.org/index.php/Technical_Risks_of_Reverse_Engineering_and_Unauthorized_Code_Modification
- OWASP Reverse Engineering and Code Modification Prevention - https://www.owasp.org/index.php/OWASP_Reverse_Engineering_and_Code_Modification_Prevention_Project
