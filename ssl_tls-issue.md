# Troubleshooting SSL/TLS Errors in Ansible

This document provides steps to troubleshoot SSL/TLS errors that may arise while using Ansible. SSL/TLS errors typically occur when Ansible attempts to connect to a remote server using HTTPS and there are issues with the SSL/TLS certificates or configurations.

## Table of Contents
- [Introduction](#introduction)
- [Common SSL/TLS Errors in Ansible](#common-ssltls-errors-in-ansible)
- [Troubleshooting Steps](#troubleshooting-steps)
  - [Step 1: Verify SSL/TLS Certificate](#step-1-verify-ssltls-certificate)
  - [Step 2: Check the Certificate Path](#step-2-check-the-certificate-path)
  - [Step 3: Disable SSL Verification (if necessary)](#step-3-disable-ssl-verification-if-necessary)
  - [Step 4: Update Python SSL Libraries](#step-4-update-python-ssl-libraries)
  - [Step 5: Verify System Time](#step-5-verify-system-time)
- [Conclusion](#conclusion)

## Introduction

SSL/TLS errors in Ansible may occur during playbook execution when Ansible communicates over HTTPS, particularly with web services or APIs. These errors can happen due to expired certificates, misconfigured paths, or Python libraries that don't support newer versions of SSL/TLS. 

The following steps will guide you in troubleshooting and resolving SSL/TLS errors.

## Common SSL/TLS Errors in Ansible

- **SSL certificate verification failed**: This error usually indicates that the SSL certificate provided by the remote server cannot be verified by the local machine.
- **SSL/TLS handshake failed**: This error typically occurs if there's an issue during the handshake between the client (Ansible) and the server, possibly due to incompatible SSL/TLS protocols.
- **Unable to get local issuer certificate**: This indicates that Ansible cannot find a valid certificate chain, or the root certificate is missing.
- **SSL Error: Unable to get the local issuer certificate**: Common when using Ansible with HTTPS API endpoints or when Ansible cannot validate the server's SSL certificate.

## Troubleshooting Steps

### Step 1: Verify SSL/TLS Certificate

To check the SSL certificate for the remote server, run the following command:

```bash
openssl s_client -connect <hostname>:443
```


### Step 2: Check the Certificate Path
If Ansible is unable to validate the certificate, ensure that your system trusts the CA (Certificate Authority) that issued the certificate. Check the following:

On Linux systems, you can find the trusted CA certificates in /etc/ssl/certs or /etc/pki/tls/certs.
