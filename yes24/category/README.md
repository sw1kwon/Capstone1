# YES24 Category Data

- This repository contains daily snapshots of book category data crawled from [YES24/IT Mobile](https://www.yes24.com/Product/Category/Display/001001003).  
- The data includes product counts by category, collected every day at 05:00 and 17:00 (KST).
- The data includes product counts by category and subcategory, collected every day at 05:15 and 17:15 (KST).

## Files
- `ctgr_YYYYMM_DD_HH.csv`: Parent categories
- `subctgr_YYYYMM_DD_HH.csv`: Subcategories

## Schedule
- Crawled twice daily using an automated scheduler
- All data is saved in UTF-8 with BOM format
