# Getting Started with Vault

**Lab Duration:** 1 hour  
**Difficulty:** Introductory  
**No cost**

---

## Overview

This lab introduces **HashiCorp Vault**, a powerful identity-based secrets and encryption management system. Vault secures, stores, and tightly controls access to sensitive information such as API keys, passwords, certificates, and encryption keys. It supports dynamic secrets, encryption services, and fine-grained access control through authentication and authorization methods.

Vault helps solve challenges related to secret management across complex, dynamic infrastructures by offering:

- Secure secret storage with encryption-at-rest  
- Dynamic secrets generation and automatic revocation  
- Leasing and renewal of secrets to enforce lifecycle policies  
- Encryption-as-a-Service through the Transit secrets engine  
- Robust authentication methods for identity verification  
- Auditability and detailed access logging  

---

## What This Lab Teaches

- Installing and running Vault in development mode on Cloud Shell  
- Enabling and managing **Key/Value (KV)** secret engines to store, version, and retrieve arbitrary secrets  
- Creating, reading, updating, deleting, and destroying secrets with Vault CLI  
- Managing secrets versions and metadata  
- Enabling and working with Vault **secrets engines** such as Transit for encryption operations  
- Understanding and configuring Vault authentication methods including token and userpass authentication  
- Creating and revoking tokens for secure Vault access  
- Using the Vault web UI to manage secrets and authentication  
- Encrypting and decrypting data using the Transit secrets engine (“Encryption as a Service”)  
- Setting up user credentials and login using the userpass auth method  

---

## Core Concepts and Components

- **Vault Server:** The main service that manages access control and secret storage; in this lab, run in *dev mode* for easy experimentation.  
- **Secrets Engines:** Plugins that provide different ways of storing or generating secrets, e.g., KV store, Transit encryption engine, dynamic database credentials.  
- **Key/Value Secrets Engine (kv-v2):** Generic secret store that supports versioned storing and retrieval of arbitrary keys and values.  
- **Tokens:** Authentication tokens that represent sessions with associated policies and capabilities.  
- **Authentication Methods:** Various ways to authenticate users/services such as token, userpass, GitHub, AppRole, etc.  
- **Transit Secrets Engine:** Provides cryptographic operations for encryption, decryption, signing, and verification without storing the data itself.  
- **Policies:** Vault authorization rules that govern what authenticated users or tokens can access or perform (covered in later labs).  

---

## Key Commands and Workflow Highlights

- **Starting Vault in development mode:**
```
vault server -dev
```

- **Setting environment variables for Vault interaction:**
```
export VAULT_ADDR='http://127.0.0.1:8200'
export VAULT_TOKEN='<root-token-from-server-startup>'
```

- **Managing KV secrets:**

- Write secret:  
  `vault kv put secret/hello foo=world`

- Read secret:  
  `vault kv get secret/hello`

- Delete secret:  
  `vault kv delete secret/hello`

- List secrets:  
  `vault kv list secret/`

- **Enable a new secrets engine (kv):**
```
vault secrets enable -path=kv kv
```

- **Manage tokens:**

- Create token:  
  `vault token create`

- Revoke token:  
  `vault token revoke <token>`

- **Enable userpass auth and create user:**
```
vault auth enable userpass
vault write auth/userpass/users/admin password=password! policies=admin
```

- **Encrypt/decrypt using Transit secrets engine via the Vault UI in Cloud Shell Web Preview**

---

## What I Learned

- How Vault secures sensitive data with encryption both at rest and in transit.  
- Versioned secret management enables auditability and rollback of secret data.  
- Vault’s architecture separates secret storage from secret access through pluggable secrets engines and authentication backends.  
- The importance of dynamic secrets and secret revocation in reducing the blast radius of compromised credentials.  
- How to use Vault’s CLI and web UI for managing secrets and auth methods effectively.  
- Best practices around authenticating clients and assigning least privilege policies (to be explored later).  
- How Vault’s transit engine can offload complex encryption tasks from applications via cryptographic-as-a-service.  

---

This lab builds foundational knowledge and skills in Vault operations, preparing you to apply secret management and encryption seamlessly within cloud and enterprise environments.
