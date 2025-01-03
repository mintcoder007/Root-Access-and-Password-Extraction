# Root-Access-and-Password-Extraction
# Pentesting Report: Flag Extraction

## Objective:

The goal of this pentest was to gain root access to the target system and extract two flags, including the root flag, using manual exploitation techniques.

## Steps Taken:

### 1. Boot into Single User Mode:

- Accessed the boot menu using `F12` during system startup.
- Edited the boot parameters by:
  - Identifying the line starting with `linux` (ending with `maybe-abiquity`).
  - Replacing `ro` with `rw` to enable read-write access.
  - Appending `init=/bin/bash` at the end of the line.
- Booted into the root shell.

### 2. Navigating the Filesystem:

- Used the command `ls -al` to list files and directories in the root filesystem.

### 3. Extraction of User Flag:

- Navigated to the `/home/dave` directory:
  - Executed `cd /home/dave`.
  - Listed the contents using `ls -la`.
- Identified the flag file `f1ag.txt`.
- Extracted the contents of the file using:
  ```bash
  cat f1ag.txt
  ```
  - Output: `c51f6399513526eaaaab5a4701050f22e49`

### 4. Extraction of Root Flag:

- Navigated to the root directory:
  - Executed `cd /root`.
  - Listed the contents using `ls`.
- Identified the root flag file `r_flag.txt`.
- Extracted the contents of the file using:
  ```bash
  cat r_flag.txt
  ```
  - Output: `eacb474b122937f83b04d9500cf2c23b8940c2d3a79c57d928d4472089df2cc`

## Results:

### Flags Extracted:

1. User Flag: `c51f6399513526eaaaab5a4701050f22e49`
2. Root Flag: `eacb474b122937f83b04d9500cf2c23b8940c2d3a79c57d928d4472089df2cc`

## Observations:

- The system was vulnerable due to misconfigured boot parameters, allowing access to single-user mode and direct root shell.
- Flag files were unprotected and easily accessible once root access was obtained.

## Recommendations:

1. **Secure Boot Configuration**:
   - Password-protect the bootloader to prevent unauthorized edits to boot parameters.
2. **Restrict Single User Mode Access**:
   - Require authentication for single-user mode.
3. **Protect Sensitive Files**:
   - Set appropriate permissions to restrict access to flag files and other sensitive data.
4. **Monitor Logs**:
   - Regularly review system logs to detect unauthorized access attempts.

---

**Note:** This report is based on a controlled pentesting environment. Implement recommended security measures to safeguard your system from unauthorized access
