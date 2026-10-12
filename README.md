# Columnar_Cipher
## 📝 About the Algorithm: Columnar Transposition Cipher

The **Columnar Transposition Cipher** is a symmetric encryption algorithm that scrambles the positions of the characters (transposition) rather than altering the characters themselves (substitution).

The core of this algorithm relies on a **Keyword**. This keyword is used to structure a grid and determine the exact order in which the columns are read. Without knowing the keyword, it is computationally difficult to reconstruct the original message.

---

### 🔒 How it Works

#### 1. Encryption Phase
* **Define Column Order:** The letters of the keyword are sorted alphabetically to assign a numerical priority to each column.
* **Build the Grid:** The plaintext (without spaces) is written row by row (from left to right) into a grid where the number of columns equals the length of the keyword.
* **Padding:** If the final row is incomplete, dummy characters (often `X`) are appended to fill the empty cells to complete the grid.
* **Extract Ciphertext:** The grid is read **column by column** based on the numerical priority derived from the keyword's alphabetical order.

#### 2. Decryption Phase
* Calculate the required number of rows based on the length of the ciphertext and the length of the keyword.
* Divide the ciphertext into segments (representing columns) and insert them back into the grid according to the keyword's alphabetical order.
* Read the reconstructed grid **row by row** (from left to right) to retrieve the original plaintext, ignoring any trailing padding characters at the end.

---

### 💡 Practical Example

* **Plaintext:** `HELLO WORLD` (Written as: `HELLOWORLD`)
* **Keyword:** `HACK`
* **Alphabetical Order:** A=1, C=2, H=3, K=4

**The Grid (During Encryption):**

| H (3) | A (1) | C (2) | K (4) |
| :---: | :---: | :---: | :---: |
| H | E | L | L |
| O | W | O | R |
| L | D | X | X | *(X used for padding)*

**Extracting the Ciphertext:**
Read the columns in alphabetical order (1 ➔ 2 ➔ 3 ➔ 4):
1. Column A (1): `EWD`
2. Column C (2): `LOX`
3. Column H (3): `HOL`
4. Column K (4): `LRX`

**Final Ciphertext:** `EWDLOXHOLLRX` 
