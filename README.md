# Pipeline Builder - Backend

This backend is built using FastAPI. It processes pipeline data and returns:

- Number of nodes  
- Number of edges  
- Whether the pipeline is a DAG (no cycles)  

---

## Setup

### 1. Clone Repository

```bash
git clone https://github.com/your-username/pipeline-builder.git
cd pipeline-builder/backend
2. Create Virtual Environment (Recommended)
python -m venv venv
```
### 2. Activate the environment:

Mac/Linux
```bash
source venv/bin/activate
```
Windows
```bash
venv\Scripts\activate
```
### 3. Install Dependencies
```bash
pip install fastapi uvicorn
```
### 4. Run the Server
```bash
uvicorn main:app --reload
```
## 5. Server will start at:
http://127.0.0.1:8000

## API Endpoints
Health Check
```bash
GET /
```
Response:
```bash
{
  "Ping": "Pong"
}
```
Parse Pipeline
```bash
POST /pipelines/parse
```
# Request Body
```bash
{
  "nodes": [
    { "id": "input-1" },
    { "id": "llm-1" }
  ],
  "edges": [
    { "source": "input-1", "target": "llm-1" }
  ]
}
```
# Response
```bash
{
  "num_nodes": 2,
  "num_edges": 1,
  "is_dag": true
}

```
## DAG Validation Logic

Uses Depth-First Search (DFS)
If a cycle exists → Not a DAG
If no cycle → Valid DAG

# API Testing

Swagger UI available at:
```bash
http://127.0.0.1:8000/docs
```

## Future Improvements
- Real-time validation
- Graph visualization
- Cycle detection UI
- Authentication & authorization

# Author
Anchal Yadav
