## Intent

This pattern defines how systems MUST handle the lifecycle of credentials that are locally released by biometric authentication.

Biometric data and biometric templates must remain protected private data within the local trusted execution environment, secure element, secure enclave, or an equivalent protected component.

This pattern focuses on the lifecycle of the security-relevant digital artifacts around biometric authentication: enrollment state, credential binding, assurance state, revocation, re-enrollment, audit evidence, and user notification.

The goal is to ensure that biometric authentication can be used in a trusfull, transparent, accountable, and privacy-preserving way while maintaining confidentiality, integrity, and availability. The security model should follow Kerckhoffs’ principle: the it architecture, lifecycle rules, revocation logic, and evidence model MUST be understandable and reviewable without disclosing secrets, private keys, biometric templates, or biometric raw data.

In case of suspected compromise, the affected credential binding must be revocable, the assurance state must be updated, and the user must be informed in clear and understandable language. A new trusted enrollment or credential binding must then be established through a controlled re-enrollment process.



**Requirement: Secure Lifecycle of Biometric Authentication Artifacts**

A system that uses **biometric authentication** MUST process raw biometric data exclusively locally within a secure execution environment and derive a non-reversible, secure biometric template or biometric reference from it.

The biometric template MUST NOT leave the device unprotected and MUST NOT be transmitted to services as proof of authentication. Authentication with services MUST be performed using cryptographic credentials, actually trusted secure encryption and the use of which is authorized locally via biometrics, a device PIN, or an equivalent trustfull method.

Every creation, modification, deactivation, or deletion of a biometric template MUST be logged as a security-relevant lifecycle event. The log MUST contain at least the time, event type, affected credential reference, device reference, trust status, and follow-up action, without disclosing raw biometric data or reconstructible template data.

If a compromise is suspected, the affected biometric authentication artifact or the cryptographic credential bound to it MUST be revoked immediately, marked as untrusted, and blocked for further authentication. Subsequently, a new enrollment process MUST be performed with a new, versioned, and cryptographically bound replacement artifact.

Affected users MUST be informed in clear, understandable, and transparent process about the issue, scope, risks, and necessary protective measures. The information MUST explain which artifact is affected, which accesses have been revoked, what re-authentication is required, and what further steps are recommended.

The it architecture MUST permanently ensure confidentiality, integrity, and availability while adhering to the Kerckhoffs principle: The security model, protective measures, event logic, and revocation processes MUST be documented in a traceable manner without disclosing secret keys, templates, or raw personal data.
