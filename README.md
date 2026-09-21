## Overview

This project documents my Week 3 cybersecurity lab on **password cracking and password security**. I worked with two approaches:

1. **John the Ripper (JTR)** on Kali Linux.
2. **Networkwalks Hash Calculator and Password Cracker** through a web browser.

The purpose of the lab was to understand how a password-protected PDF can be analyzed, how its password hash can be extracted, and how password-cracking tools can test the strength of the password.

> **Ethical note:** These techniques were performed only against the password-protected files provided for the authorized training lab. They should not be used against files, accounts, or systems without permission.

## Objectives

- Understand the difference between encryption and hashing.
- Extract a PDF password hash for authorized testing.
- Use a wordlist with John the Ripper.
- Recover passwords from the provided lab hashes.
- Use browser-based password-cracking tools.
- Observe how password complexity affects cracking time.
- Understand why strong, unique passwords are important.

## Tools Used

### John the Ripper

John the Ripper (JTR) is a password-cracking tool used by security professionals to test password strength. The lab material explains that JTR supports different hash types and can also work with password-protected files such as PDFs, ZIP files, and Office documents.

For the Kali Linux portion, I used:

- Kali Linux
- John the Ripper
- `rockyou.txt` wordlist
- PDF password hashes stored in `.txt` files

The lab instructions also introduced **Johnny**, the graphical interface for John the Ripper.

### Networkwalks Tools

The second approach used two browser-based tools:

- **Hash Calculator**:extracts the PDF hash.
- **Password Cracker**:attempts to recover the password from the extracted hash.

No local installation was required for this part of the lab.

## Method 1 (John the Ripper)

### 1. Prepare the password hash

The protected PDF was converted into a PDF-compatible hash. The resulting hash was saved in text files such as:

```text
hash1.txt
hash2.txt
hash3.txt
```

The hash was stored in the format beginning with:

```text
$pdf$...
```

### 2. Run John the Ripper

I used the `rockyou.txt` wordlist with John:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt
```

The same approach was used for the other provided hashes:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash2.txt
john --wordlist=/usr/share/wordlists/rockyou.txt hash3.txt
```

### 3. Observe the results

The terminal output showed John completing the cracking process and displaying the recovered passwords.



## Method 2 ( Networkwalks Tools )

The second method followed the browser-based workflow from the training material.

### Step 1:Extract the hash

The protected PDF was uploaded to the Networkwalks Hash Calculator.

The tool returned a hash beginning with:

```text
$pdf$...
```

### Step 2:Copy the complete hash

The complete hash was copied for use in the password-cracking stage.

### Step 3:Crack the hash

The hash was pasted into the Networkwalks Password Cracker and the attack was started.

The tool attempted different password candidates until it found a matching password.

### Step 4:Verify the password

The recovered password was then used to open the supplied protected PDF.

## What I Learned

### 1. Password complexity matters

The lab demonstrated that simple or commonly used passwords can be recovered relatively quickly when they appear in a wordlist.

This reinforces the importance of using passwords that are:

- Long
- Unique
- Difficult to guess
- Not based on common words or predictable patterns

### 2. Wordlists are useful in password auditing

Using `rockyou.txt` demonstrated how a wordlist can be used to test passwords against known/common candidates.

### 3. Hashes are not the same as encryption

The lab material distinguishes hashing from encryption. Encryption is designed to be reversible with the appropriate key, while hashing produces a one-way message digest.

### 4. Password cracking is useful for defensive security

Password cracking is not only an offensive technique. In an authorized security assessment, it can help identify weak passwords and demonstrate where stronger authentication practices are needed.

## Challenges / Observations

- Password-cracking speed varied between hashes.
- The complexity and position of a password in the wordlist affected how quickly it was recovered.
- Correct hash formatting was important. Extra characters could prevent the tool from processing the hash correctly.
- Running the same task through JTR and a browser-based tool helped me understand the workflow from two different perspectives.



## Key Takeaway

This project gave me practical exposure to **password auditing, hashing, wordlists, and John the Ripper**. More importantly, it showed how easily weak or predictable passwords can be recovered in an authorized testing environment.

The main lesson is simple: password strength is an important part of an organization's security posture.

## Lab Source

This project was completed as part of the **Networkwalks Cybersecurity & Ethical Hacking – Week 3 Project Module**.

