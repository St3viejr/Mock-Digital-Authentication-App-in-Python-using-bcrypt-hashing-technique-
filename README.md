# Secure Password Storage (Python + Bcrypt)

This project demonstrates how to securely handle user credentials using **Hashing** and **Salting**. It implements a mock authentication system that stores user data in a text file, ensuring that **plain text passwords are never stored**.

It uses the industry-standard **bcrypt** library, which employs adaptive hashing to defend against brute-force and rainbow table attacks.

---

### Skills Demonstrated

* **Python:** File I/O (reading/writing text databases), String manipulation, CLI Logic.
* **Cybersecurity:**
    * **Hashing vs. Encryption:** Understanding one-way functions.
    * **Salting:** Preventing Rainbow Table attacks by adding random data to hashes.
    * **Key Stretching:** Using `bcrypt` to slow down brute-force attempts.
    * **Credential Management:** Securely verifying passwords without storing them.

---

### Project Structure

* **`password_storage.py`**: The main script containing the registration and authentication logic.
* **`users.txt`**: The "database" file. It stores records in the format: `username,hashed_password,salt`.

---

### How to Run

1.  **Install Dependencies:**
    This project requires the `bcrypt` library.
    ```bash
    pip install bcrypt
    ```
2.  **Run the Script:**
    ```bash
    python password_storage.py
    ```
3.  **Use the Menu:**
    * **Option 1:** Register a new user (Generates Salt + Hash).
    * **Option 2:** Log in (Verifies Password against Hash).
    * **Option 3:** Exit.

---

### How it Works (The Logic)

1.  **Registration:**
    * User inputs password: `mysecret`
    * System generates random salt: `AbCdEf...`
    * System calculates: `Bcrypt(mysecret + AbCdEf...)` -> `Hash123...`
    * System saves: `username, Hash123..., AbCdEf...`

2.  **Authentication:**
    * User inputs password: `mysecret`
    * System looks up username and retrieves the stored salt: `AbCdEf...`
    * System calculates: `Bcrypt(input + AbCdEf...)`
    * System compares the result to the stored `Hash123...`. If they match, the password is valid.
