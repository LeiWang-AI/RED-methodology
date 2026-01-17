# Software Engineering Primitive Registry

A curated set of atomic operations for software engineering contexts.

---

## File Operations

| Primitive | Description | Tool Exists? | Knowledge Required |
|-----------|-------------|--------------|-------------------|
| `read_file(path)` | Read contents of a file | fs/OS | File path syntax |
| `write_file(path, content)` | Write content to a file | fs/OS | File path, permissions |
| `list_files(path)` | List files in directory | fs/OS | Directory structure |
| `delete_file(path)` | Remove a file | fs/OS | Permissions |
| `file_exists(path)` | Check if file exists | fs/OS | Path syntax |

---

## Database Operations

| Primitive | Description | Tool Exists? | Knowledge Required |
|-----------|-------------|--------------|-------------------|
| `query_db(sql)` | Execute SQL query | DB client | SQL syntax |
| `insert_record(table, data)` | Insert a record | DB client | Schema |
| `update_record(table, id, data)` | Update a record | DB client | Schema, keys |
| `delete_record(table, id)` | Delete a record | DB client | Schema, keys |
| `apply_migration(name)` | Run a database migration | Migration tool | Migration format |

---

## Code Operations

| Primitive | Description | Tool Exists? | Knowledge Required |
|-----------|-------------|--------------|-------------------|
| `run_tests(pattern)` | Execute test suite | Test runner | Test framework |
| `lint_code(path)` | Run linter on code | Linter | Config format |
| `build_project()` | Compile/build project | Build tool | Build config |
| `deploy(target)` | Deploy to environment | Deploy tool | Target config |

---

## Search Operations

| Primitive | Description | Tool Exists? | Knowledge Required |
|-----------|-------------|--------------|-------------------|
| `search_files(query)` | Search file contents | grep/ripgrep | Regex syntax |
| `search_codebase(symbol)` | Find symbol definitions | LSP/ctags | Symbol naming |
| `git_log(options)` | Query git history | git | Git commands |
| `git_diff(ref1, ref2)` | Compare versions | git | Git refs |

---

## API Operations

| Primitive | Description | Tool Exists? | Knowledge Required |
|-----------|-------------|--------------|-------------------|
| `http_get(url)` | Make GET request | HTTP client | URL, headers |
| `http_post(url, body)` | Make POST request | HTTP client | URL, body format |
| `authenticate(credentials)` | Obtain auth token | Auth service | Auth flow |

---

## Verification Operations

| Primitive | Description | Tool Exists? | Knowledge Required |
|-----------|-------------|--------------|-------------------|
| `hash(content)` | Compute hash of content | Hash library | Hash algorithm |
| `diff(a, b)` | Compare two texts | Diff tool | Diff format |
| `validate_json(content, schema)` | Validate against schema | JSON validator | JSON Schema |

---

## How to Use This Registry

1. **During decomposition:** Stop when you reach a primitive from this list
2. **During audit:** Verify each column (Tool Exists?, Knowledge Required)
3. **Extend as needed:** Add domain-specific primitives for your context

---

## Registry Evolution

This registry grows through failure-driven refinement:
- When an action fails because it wasn't primitive enough → add the missing primitive
- When verification fails → refine the knowledge/tool requirements
- When a new domain is encountered → create a domain-specific extension

---

## Contributing

Submit PRs to add primitives for other domains:
- DevOps / Infrastructure
- Data Engineering
- Machine Learning
- Frontend / UI

