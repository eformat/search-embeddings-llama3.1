# search-embeddings-llama3.1

Uses spotify [annoy](https://github.com/spotify/annoy) to search for Approximate Nearest Neighbors based on llama3.1 embeddings. Stores the data in sqlite3 and annoy index file.

# Demo

Run a local llama model with embeddings turned on

```bash
python3 -m llama_cpp.server \
  --model ~/instructlab/models/Meta-Llama-3.1-8B-Instruct-Q5_K_M.gguf \
  --n_gpu_layers=-1 \
  --chat_format llama-3 \
  --n_ctx 4096 \
  --port 8080 \
  --embedding True
```

Run app - first invocation will create db and index `large_text_file.txt`

```bash
python app.py
```

Query for similarity

```bash
$ python app.py 
Rebuilding Annoy index...
Rebuilding Annoy index...
Added 0/94 vectors to the index
Building index...
Index built and saved
Annoy index rebuilt.

1. Add a question
2. Find similar questions
3. Exit
Enter your choice (1-3): 2
Enter your query: Erik Larsson, 44, carpenter, builds custom furniture as a hobby.

Top 5 similar texts to 'Erik Larsson, 44, carpenter, builds custom furniture as a hobby.':
ID: 20, Similarity: 1.0000
Text: Erik Larsson, 44, carpenter, builds custom furniture as a hobby....

ID: 27, Similarity: 1.0000
Text: Elena Popov, 40, violinist, performs with a renowned orchestra....

ID: 82, Similarity: 1.0000
Text: Erik Johansson, 43, nature photographer, captures Nordic landscapes....

ID: 93, Similarity: 1.0000
Text: Elena Rodriguez, 42, flamenco dancer, preserves traditional Andalusian art....

ID: 16, Similarity: 0.8452
Text: Kwame Osei, 48, journalist, covers international politics....
```
