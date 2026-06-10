# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600874
**Name:** Cao Văn Hảo
**Date:** 2026-06-10

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Ket qua chinh xac, Laptop la san pham electronics dat nhat trong du lieu sach |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Ket qua sai hoan toan, Agent tra ve san pham khong hop ly voi gia bat thuong |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi su dung garbage data, Agent da tra ve ket qua hoan toan sai vi nhieu ly do lien quan den chat luong du lieu dau vao. Thu nhat, du lieu chua **Duplicate IDs** — record id=1 xuat hien hai lan (Laptop va Banana), dieu nay gay nham lan khi Agent truy van. Thu hai, co **wrong data types** nhu truong price cua "Broken Chair" la "ten dollars" thay vi so, khien viec so sanh gia bi loi. Thu ba, du lieu co **outliers** nghiem trong nhu "Nuclear Reactor" voi gia 999999 — mot gia tri bat thuong khong phan anh thuc te, nhung Agent van chon no la san pham tot nhat vi don gian no co gia cao nhat. Thu tu, co **null values** nhu record "Ghost Item" khong co id va khong co category, gia bang 0. Tat ca nhung van de nay chung minh rang neu du lieu dau vao khong duoc validate va lam sach truoc khi dua vao he thong, Agent se dua ra nhung quyet dinh sai lam nghiem trong. Pipeline ETL voi buoc validation la vo cung quan trong de dam bao chat luong output.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y. Du prompt co tot den dau, neu du lieu dau vao chua nhieu loi (duplicate, outlier, null, sai kieu du lieu), Agent van se tra ve ket qua sai. Viec dam bao chat luong du lieu thong qua ETL pipeline va data validation la buoc tien quyet truoc khi su dung bat ky mo hinh AI nao.
