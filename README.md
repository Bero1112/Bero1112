- 👋 Hi, I’m @Bero1112
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Bero1112/Bero1112 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import hashlib
import random
import time

def generate_hash(data):
  """Генерира хеш на данни.

  Args:
    data: Данните, за които да се генерира хеш.

  Returns:
    Хеша на данните.
  """

  return hashlib.sha256(data.encode()).hexdigest()

def mine_block(previous_hash, transactions):
  """Изкопава блок.

  Args:
    previous_hash: Хешът на предишния блок.
    transactions: Списък с транзакциите за блока.

  Returns:
    Блокът, който е изкопан.
  """

  nonce = 0
  while True:
    block_header = {
        "previous_hash": previous_hash,
        "timestamp": time.time(),
        "nonce": nonce,
        "transactions": transactions,
    }
    block_hash = generate_hash(str(block_header))
    if block_hash.startswith("0000"):
      return block_header
    nonce += 1

def create_coint(initial_supply):
  """Създава койнт.

  Args:
    initial_supply: Началната поставка на койнта.

  Returns:
    Койнта, който е създаден.
  """

  genesis_block = mine_block("0", [])
  coint = {
    "genesis_block": genesis_block,
    "transactions": [],
    "supply": initial_supply,
  }
  return coint

# 
coint = create_coint(1000000)

#
print("Койнт:", coint)
print("Генезис блок:", coint["genesis_block"])
print("Трансакции:", coint["transactions"])
print("Поставка:", coint["supply"])
