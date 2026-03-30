
conda:
conda create -p venv python==3.12
conda activate .....venv 
conda deactivate
pip install -r requirements.txt


uv:
uv init <project-name>
uv venv 
source venv/bin/activate 
uv add <package name>