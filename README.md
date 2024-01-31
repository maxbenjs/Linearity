# Linearity
---

# Files & Directories
---

- Data directory containing csv's of the 2 datasets
- Task description PDF
- Jupyter Analysis Notebook
- Metabase Dashboard PDF

# Answers
---
```python
# Database connection params
host='linearity-postgres.ci4darskkd34.eu-central-1.rds.amazonaws.com'
port=5432
database='tempdb'
username='linearity-home-assignment-user'
password='e0a1bf24bb7a81de7ac81834343ad6169711366863e0f6d66f71f2280e314668'

# Create db connection engine
try:
    engine = create_engine(f"postgresql+psycopg2://{username}:{password}@{host}:{port}/{database}")
except Exception as e:
    print(e)
```

