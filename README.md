"""
README for Material Advisor

Overview
--------
Material Advisor ranks sustainable building materials using a hybrid recommender:
- Collaborative filtering via LightFM on historical project-material usage
- Content retrieval of material features (cost, carbon footprint)

The tool loads data from a SQL database (SQLite by default), trains the LightFM model,
and outputs top-N material recommendations for a specified project.

Requirements
------------
- Python 3.12
- pandas
- numpy
- scipy
- lightfm
- sqlalchemy

Installation
------------
pip install pandas numpy scipy lightfm sqlalchemy

Usage
-----
# (Optional) Initialize the SQLite database from CSVs:
python material_advisor.py --init \
    --materials data/materials.csv \
    --interactions data/interactions.csv \
    --db sqlite:///materials.db

# Train model and recommend top 10 for project ID 1:
python material_advisor.py \
    --db sqlite:///materials.db \
    --epochs 30 \
    --components 20 \
    --project-id 1 \
    --top-n 10

Outputs
-------
- Trained model saved as `lightfm_model.npz`
- `recommended_materials.csv`: top-N materials with predicted scores, cost, and carbon footprint
"""
