[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112765&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** AI20K-2A202600874
**Name:** Cao Văn Hảo

---

## Mo ta

Bai lab nay xay dung mot ETL Pipeline tu dong de xu ly du lieu san pham. Pipeline doc du lieu tu file JSON, thuc hien validation de loai bo cac record khong hop le (gia <= 0 hoac category rong), transform du lieu (tinh gia giam 10% va chuan hoa category thanh Title Case), va luu ket qua ra file CSV. Ngoai ra, bai lab con thuc hien thi nghiem stress test de so sanh ket qua cua AI Agent khi su dung du lieu sach va du lieu rac.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Chay agent voi ca 2 bo du lieu (clean va garbage)
python agent_simulation.py
```

Hoac chay thu cong de kiem tra tung scenario:
```bash
python -c "from agent_simulation import simulate_agent_response; print(simulate_agent_response('What is the best electronic product?', 'processed_data.csv'))"
python -c "from agent_simulation import simulate_agent_response; print(simulate_agent_response('What is the best electronic product?', 'garbage_data.csv'))"
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── agent_simulation.py      # Agent simulation cho stress test
├── raw_data.json            # Du lieu dau vao (5 records)
├── processed_data.csv       # Output cua pipeline (3 records hop le)
├── garbage_data.csv         # Du lieu rac de test
├── generate_garbage.py      # Script tao du lieu rac
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Tong so records dau vao:** 5
- **Records hop le (kept):** 3 (Laptop, Chair, Monitor)
- **Records bi loai (dropped):** 2
  - id=3 (Mystery Box): Price <= 0 (-$10)
  - id=4 (Phone): Category rong
- **Output:** `processed_data.csv` voi cac cot: id, product, price, category, discounted_price, processed_at
