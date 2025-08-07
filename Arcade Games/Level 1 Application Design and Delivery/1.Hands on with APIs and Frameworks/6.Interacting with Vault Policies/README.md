# Interacting with Vault Policies

**Lab Duration:** 1 hour  
**Difficulty:** Introductory  
**No cost**

---

## Overview

In this lab, you learn how to create, manage, and associate **Vault policies** to enforce fine-grained Role-Based Access Control (RBAC) within HashiCorp Vault. Policies define what actions authenticated users or machines may perform on specific paths in Vault, enabling strict control over secret access and management.

You gain hands-on experience writing policy rules using HashiCorp Configuration Language (HCL), testing permissions, and associating policies to users and tokens for practical access governance.

---

## What This Lab Teaches

- Writing Vault policies to specify allowed or denied capabilities on paths  
- Understanding policy syntax, capabilities (read, create, delete, update, list, sudo, deny)  
- Creating policies using Vault CLI and UI  
- Managing and updating policies dynamically  
- Associating policies with users/accounts to control their Vault permissions  
- Testing and verifying effective permissions via tokens  
- Implementing least privilege access by restricting policies to specific paths  
- Handling policy parameter constraints such as allowed, denied, or required keys  
- Using templated policies with identity-based variable substitution  
- Exploring Vault’s default root and default policies to understand baseline permissions  

---

## Key Concepts and Components

- **Policy:** A declarative set of rules defining which Vault paths a token or user can access and what actions they can perform.  
- **Path:** The specific Vault resource or API endpoint accessed; policies control access on a per-path basis using exact or glob patterns.  
- **Capabilities:** Actions permitted on paths, including `create`, `read`, `update`, `delete`, `list`, `patch`, `sudo`, and `deny`.  
- **Tokens:** Authentication credentials to Vault that hold sets of policies dictating access rights.  
- **RBAC (Role-Based Access Control):** Security model enforced through policies that grant fine-grained permissions to users and applications.  
- **Templated Policies:** Policies that include variables referencing identity metadata, enabling dynamic and user-specific rules.  
- **Vault CLI & UI:** Tools to create, update, delete, and inspect policies and manage user associations.  

---

## Important Commands and Workflow Highlights

- **Writing a simple read-only policy for a secret path:**

path "secret/foo" {
capabilities = ["read"]
}

text

- **Creating a new policy using CLI:**

vault policy write example-policy example-policy.hcl

text

- **Updating existing policy:**

vault policy write example-policy example-policy.hcl

text

- **Listing policies:**

vault policy list

text

- **Associating policies with users via userpass auth:**

vault write auth/userpass/users/username password="pass" policies="default,custom-policy"

text

- **Logging in to Vault with policies assigned:**

vault login -method=userpass username="username" password="pass"

text

- **Checking token policy capabilities on a path:**

vault token capabilities <token> path/to/resource

text

- **Deleting a policy:**

vault delete sys/policy/policy-name

text

---

## What I Learned

- Vault policies provide **fine-grained control** over what authenticated users and tokens can do, which paths they can access, and with what permissions—enforcing security best practices through RBAC.
- The **deny** capability can explicitly block access even if broader rules allow it, enabling precise exception management.
- Policies use path matching with wildcards/globs, enabling control over entire namespaces or very specific resources.
- Real-time policy enforcement means changes take effect immediately without needing to reissue tokens.
- Associating policies with users and tokens defines what secrets and actions are available, supporting **least privilege access**.
- Templated policies allow **dynamic, user- or entity-specific** permission generation based on identity metadata.
- Defining separate policies for different roles (e.g., `admin`, `appdev`, `security`) helps segment duties and access boundaries.
- Testing token capabilities helps verify correct policy enforcement and avoids unintended access.
- Managing policies is crucial for securing Vault environments by reducing root or overly broad access and controlling secret exposure carefully.

---

## Summary

This lab provided a comprehensive introduction to Vault’s powerful policy system, essential for secure and scalable secret management. Through writing, managing, and associating policies, you have learned how to govern access patterns in Vault, enforce RBAC, and support secure application and organization workflows.

With these skills, you can confidently design and maintain Vault authorization policies tailored to your organizational or application security requirements.

---