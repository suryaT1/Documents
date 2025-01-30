# Troubleshooting `umask 77` Issue

This document provides troubleshooting steps for addressing issues related to `umask 77` on Unix-based systems. `umask 77` can cause file permission problems when creating files or directories, often leading to unintended file access restrictions. This guide will help you identify and resolve these issues.

## check whether ansible userid password got expired or locked

```
chage -l <userid >

```
#If password is expired 

```
passwd <userid>
```

## Table of Contents
- [Introduction](#introduction)
- [Understanding `umask 77`](#understanding-umask-77)
- [Symptoms of the `umask 77` Issue](#symptoms-of-the-umask-77-issue)
- [Troubleshooting Steps](#troubleshooting-steps)
  - [Step 1: Check the Current `umask`](#step-1-check-the-current-umask)
  - [Step 2: Inspect Configuration Files](#step-2-inspect-configuration-files)
  - [Step 3: Adjust `umask` in Shell Profile](#step-3-adjust-umask-in-shell-profile)
  - [Step 4: Verify Permissions on Files](#step-4-verify-permissions-on-files)
  - [Step 5: Test the Fix](#step-5-test-the-fix)
- [Conclusion](#conclusion)

## Introduction

`umask` (user file creation mask) is a command that sets the default file permissions for newly created files and directories. A `umask` value of `77` causes files and directories to be created with restrictive permissions, making them unreadable and inaccessible to others. This document outlines how to troubleshoot and resolve issues caused by `umask 77`.

## Understanding `umask 77`

When a `umask` value of `77` is set, it means:

- **File permissions**: Files will be created with permissions `600` (rw-------).
- **Directory permissions**: Directories will be created with permissions `700` (rwx------).

This can cause problems when files or directories need to be accessible by others, or when specific permission settings are required.

## Symptoms of the `umask 77` Issue

You may encounter the following symptoms if `umask 77` is set incorrectly:

- Newly created files are not readable or writable by others.
- Files and directories are inaccessible by users who should have permissions.
- Ansible, scripts, or applications fail due to permission issues when creating or modifying files.

## Troubleshooting Steps

### Step 1: Check the Current `umask`

To check the current `umask` setting for your session, run:

```bash
umask
```
