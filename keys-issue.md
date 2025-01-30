# Steps to Resolve the Keys Issue on Server

This file contains the steps to resolve the keys issue on the server.

### 1. Check the User Permissions
Before proceeding, please check the permission of the user you are trying to connect with. It should always have +x permission on the **USER ID**.

---

## Steps to Solve the Issue

### IF KEYS ARE ALREADY GENERATED:

1. Switch to the `/home/<userid>/.ssh` path.
2. Check the permissions of the folder and files in the same directory.
3. There must be two files:
   - `id_rsa` - This file contains the private key information.
   - `authorized_keys` - This file contains the public key information.
4. Check the owner and permission of these two files. The Ansible user must have access to these files.
5. Copy the `id_rsa` file again into the Tower credential.

---

### IF KEYS ARE NOT GENERATED YET:

1. Switch to the `/home/<userid>/.ssh` path.
2. Generate the keys by following the below steps:
   - Run `ssh-keygen` (without a passphrase).
   - This will generate two files: `id_rsa` and `id_rsa.pub`.
   - Rename the `id_rsa.pub` file to `authorized_keys`.
3. Copy the `id_rsa` key file into Ansible and save it.
4. Ensure the following permissions are set for the files, along with the respective user permissions.

---

## Permission Settings:

```bash
chmod 700 /home/<userid>
chmod 700 /home/<userid>/.ssh
chmod 600 /home/<userid>/.ssh/authorized_keys
