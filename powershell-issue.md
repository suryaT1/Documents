# Troubleshooting PowerShell Issues in Ansible

This document provides troubleshooting steps for resolving PowerShell-related issues when running Ansible on Windows hosts. PowerShell is often used for automation tasks on Windows systems, and sometimes issues may arise due to environment configurations, execution policies, or other factors.

## Table of Contents
- [Introduction](#introduction)
- [Common PowerShell Issues in Ansible](#common-powershell-issues-in-ansible)
- [Troubleshooting Steps](#troubleshooting-steps)
  - [Step 1: Ensure PowerShell is Available on Windows Hosts](#step-1-ensure-powershell-is-available-on-windows-hosts)
  - [Step 2: Check PowerShell Execution Policy](#step-2-check-powershell-execution-policy)
  - [Step 3: Verify WinRM Configuration](#step-3-verify-winrm-configuration)
  - [Step 4: Ensure Required Modules are Installed](#step-4-ensure-required-modules-are-installed)
  - [Step 5: Run Ansible Commands with Administrative Privileges](#step-5-run-ansible-commands-with-administrative-privileges)
- [Conclusion](#conclusion)

## Introduction

Ansible uses PowerShell as the default shell for Windows hosts during automation tasks. PowerShell issues in Ansible are typically related to environment configuration, execution policies, or WinRM (Windows Remote Management) communication problems. This guide will help you troubleshoot and resolve these common issues.

## Common PowerShell Issues in Ansible

- **PowerShell not recognized**: The target Windows system does not have PowerShell installed or available in the system path.
- **Execution Policy Issues**: Ansible fails due to restrictive PowerShell execution policies that block script execution.
- **WinRM connectivity issues**: Ansible may fail to connect to the Windows system over WinRM, resulting in communication errors.
- **Missing PowerShell modules**: Ansible requires certain PowerShell modules to interact with Windows hosts (e.g., `PSWindowsUpdate`, `WinRM`).

## Troubleshooting Steps

### Step 1: Ensure PowerShell is Available on Windows Hosts

Ensure that PowerShell is installed and available on your target Windows host.

**Check PowerShell version**: On the target system, open a PowerShell window and check the version by running:

   ```powershell
   $PSVersionTable.PSVersion
   ```
# Steps

1. Get-ExecutionPolicy

2. Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
3. Get-Service winrm
4. winrm enumerate winrm/config/Listener

