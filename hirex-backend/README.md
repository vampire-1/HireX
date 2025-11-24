import os
from pydantic import BaseModel

class Settings(BaseModel):
    DATA_DIR: str = os.getenv("DATA_DIR", "./data")
    RESUME_DIR: str = os.getenv("RESUME_DIR", "./data/resumes")
    DB_URL: str = os.getenv("DB_URL", "sqlite:///./data/smarthire.db")
    EMBEDDING_MODEL: str = os.getenv("EMBEDDING_MODEL", "sentence-transformers/all-MiniLM-L6-v2")
    FAISS_INDEX_PATH: str = os.getenv("FAISS_INDEX_PATH", "./data/faiss_index.bin")
    FAISS_META_PATH: str = os.getenv("FAISS_META_PATH", "./data/faiss_meta.jsonl")

settings = Settings()

os.makedirs(settings.DATA_DIR, exist_ok=True)
os.makedirs(settings.RESUME_DIR, exist_ok=True)