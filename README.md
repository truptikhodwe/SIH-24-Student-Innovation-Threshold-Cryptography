# SIH-24-Student-Innovation-Threshold-Cryptography
Multi-Party Fund and Document Approval through Threshold Signatures

## Problem Statement
In multi-party decision-making processes, especially involving government agencies or private entities, fund allocation and document approvals are prone to misuse, corruption, or unauthorized alterations. Traditional systems, relying on a single point of approval, are vulnerable to security risks, especially when dealing with sensitive information or significant financial transactions.

## Proposed Solution
We propose a system based on threshold signatures using the Elliptic Curve Digital Signature Algorithm (ECDSA) to ensure that no single party can authorize a transaction without approval from a required threshold of participants. This approach guarantees both security and accountability in fund distribution or document authorization processes.

## Key Benefits
1. **Key Generation:**
   - Private and public keys are generated for each party using ECDSA. 
   - Each party holds a share of the key, and collectively, the parties are able to generate a threshold signature.
   
2. **Fund/Document Request Submission:**
   - A request for fund allocation or document approval is made by a party. The request contains necessary transaction details, such as amount or document type.
   
3. **Threshold Signature Generation:**
   - Approval requests are sent to participating parties. A pre-defined threshold (e.g., 3 out of 5 members) must approve the request.
   - Once the required approvals are collected, partial signatures are combined to generate a valid signature for the request.

4. **Verification and Execution:**
   - The signature is verified using the public keys of the participants.
   - If the signature is valid, the fund allocation or document is approved and executed.
   
5. **Audit and Logging:**
   - All requests and approvals are logged for audit purposes, ensuring traceability.
  
## ECDSA Implementation
We utilize ECDSA for secure key generation and the digital signature process. Each participant has a unique key pair (private and public). These are used as follows:

1. **Private Key:** Held securely by each participant. It is used to generate partial signatures.
2. **Public Key:** Used to verify the validity of the combined threshold signature.
3. **Digital Signature:** Each approved party provides a partial signature, which, when combined, forms a valid digital signature, ensuring the request's authenticity.

## ECDSA Code Steps

Here is a brief overview of how ECDSA is used in the code:

1. **Key Generation:** Using the elliptic curve cryptography, private and public keys are generated for each stakeholder.
2. **Signature Creation:** Each party signs the request with their private key, generating a partial signature.
3. **Threshold Signature Combination:** Once the required number of approvals is collected, the system combines the partial signatures into one valid signature.
4. **Signature Verification:** Using the public keys of the participants, the combined signature is verified to ensure the authenticity of the request.

The codebase contains implementations of the key generation, signing, and verification processes using ECDSA, ensuring security throughout the transaction lifecycle.

## Research and References

1. https://medium.com/keepnetwork/threshold-ecdsa-safer-more-private-multi-signatures-51153f3e9ed2
2. https://scryptplatform.medium.com/threshold-signatures-a0eff03dc29c#:~:text=A%20(t%2C%20n)%20threshold,of%20t%20or%20fewer%20cannot
3. https://github.com/bnb-chain/tss-lib
4. https://github.com/h4sh3d/poc-threshold-ecdsa-secp256k1/blob/master/ecdsa.py
5. https://github.com/NillionNetwork/tinysig/blob/main/src/tinysig/tecdsa.py
6. https://iacr.org/archive/crypto2001/21390136.pdf
7. https://eprint.iacr.org/2023/765.pdf
