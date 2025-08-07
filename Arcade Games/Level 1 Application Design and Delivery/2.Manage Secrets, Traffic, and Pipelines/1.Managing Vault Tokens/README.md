# Managing Vault Tokens

**Lab Duration:** 1 hour  
**Difficulty:** Introductory  
**No cost**

---

## Overview

This lab covers the fundamental concepts and practical management of **tokens** in HashiCorp Vault. Tokens are the core authentication method in Vault, representing identities used by clients and applications to access secrets securely. You will explore creating, using, renewing, revoking, and understanding different types of Vault tokens, such as service tokens, batch tokens, orphan tokens, and tokens with usage limits.

---

## What This Lab Teaches

- Understanding Vault tokens as authentication credentials and their role in access control  
- Creating various types of tokens: service tokens, batch tokens, orphan tokens, tokens with use limits  
- Managing token lifecycles by setting TTLs (time to live), renewing, and revoking tokens  
- Token hierarchies and the impact of parent-child relationships on token validity  
- Using token accessors to reference tokens securely  
- Applying token roles to streamline token creation with predefined policies and constraints  
- Differentiating tokens based on their characteristics and use cases to optimize Vault performance  
- Using Vault CLI commands to create, lookup, renew, revoke, and inspect tokens and their metadata  

---

## Key Concepts and Terms

- **Service Tokens:** Persistent tokens used for authentication that can be renewed and revoked.  
- **Batch Tokens:** Lightweight, non-persistent tokens which are not stored and cannot be revoked manually; best for large-scale ephemeral use.  
- **Orphan Tokens:** Tokens without a parent token; their lifecycle is independent of other tokens.  
- **Use Limit Tokens:** Tokens that expire after a specified number of uses, protecting against overuse.  
- **TTL and Max TTL:** Time-to-live and maximum time-to-live values controlling token lifespan and renewal policies.  
- **Token Accessor:** A value referencing a token that facilitates limited token management operations without exposing the token itself.  
- **Token Hierarchy:** Parent-child token relationships where revoking a parent token revokes its child tokens unless they are orphans.  

---

## Sample Commands Learned

- Create a token with TTL and use limits:
```
vault token create -ttl=1h -use-limit=2 -policy=default
```

- Renew a token’s TTL:
```
vault token renew <token>
```

- Revoke a token:
```
vault token revoke <token>
```

- Create an orphan token:
```
vault token create -orphan
```

- Create a batch token with specific TTL:
```
vault token create -type=batch -policy=test -ttl=20m
```

- Lookup token metadata:
```
vault token lookup <token>
```

- Create a token role and issue tokens:
```
vault write auth/token/roles/zabbix allowed_policies="policy1, policy2" orphan=true period=8h
vault token create -role=zabbix
```

---

## What I Learned

- Vault tokens are essential for secure authentication and controlling access within Vault.  
- Managing token lifecycles with TTLs and renewals helps enforce security and resource management.  
- Different token types serve different purposes: long-lived service tokens for persistent access, batch tokens for ephemeral use, and orphan tokens for independence from parent revocations.  
- Use limit tokens add an extra layer of security by restricting the number of allowed uses.  
- Token hierarchies and orphans affect how token revocation cascades or isolates tokens.  
- Token accessors provide a safe way to manage tokens without exposing sensitive token strings.  
- Token roles simplify token creation with predefined policies and behaviors to reduce complexity and enhance security.  
- Effective token management is crucial to maintaining the security posture and operational health of Vault-managed infrastructures.  

---

This lab equipped me with comprehensive skills to create, manage, and secure Vault tokens, a pivotal part of handling authentication and authorization in secret management systems.