# Learning Notes - Playlist Chaos Project

## Things I Learned in This Session

### 1. Understanding Application Architecture
- **Control Flow Diagrams**: How to visualize an application's data flow from start to finish
- **Component Interaction**: Understanding how different parts of an app communicate (sidebar ↔ content area ↔ session state)
- **Data Pipeline**: Inputs → Processing → Outputs at each stage
- **State Management**: How Streamlit uses session state to maintain data across re-renders

### 2. Python Virtual Environments

#### Key Concepts
- **Isolation**: Each project gets its own package versions to avoid conflicts
- **Dependency Management**: Using `requirements.txt` to share exact package versions
- **Environment Activation**: The importance of activating before installing packages

#### Practical Commands
```bash
python3 -m venv venv           # Create environment
source venv/bin/activate       # Activate (macOS/Linux)
pip install -r requirements.txt # Install dependencies
deactivate                     # Exit environment
```

#### Best Practices Learned
- ✅ Create one environment per project
- ✅ Add environment folders to `.gitignore`
- ✅ Share `requirements.txt`, not the environment itself
- ❌ Never install packages globally with sudo
- ❌ Don't commit `venv/` to version control

### 3. Streamlit Applications

#### Running a Streamlit App
```bash
streamlit run app.py
```
- Automatically opens browser at `localhost:8501`
- Hot-reloading on file changes
- Stop with `Ctrl+C`

#### Session State Pattern
- Persistent data across user interactions
- Initialize in `init_state()` function
- Access via `st.session_state.variable_name`

### 4. Project Structure & Organization

#### This Project's Architecture
```
app.py              # UI and Streamlit components
playlist_logic.py   # Business logic and data processing
requirements.txt    # Dependencies
.gitignore         # Files to exclude from git
```

#### Separation of Concerns
- **UI Layer** (app.py): Rendering, user inputs, display
- **Logic Layer** (playlist_logic.py): Data processing, algorithms
- **Configuration**: Profile settings for customization

### 5. Git & Version Control Hygiene

#### Files to Ignore
- Virtual environments (`venv/`, `.venv/`)
- Python cache files (`__pycache__/`, `*.pyc`)
- IDE settings (`.vscode/`, `.idea/`)
- Environment variables (`.env`)
- OS files (`.DS_Store`)

### 6. Application Data Flow Patterns

#### Learned Patterns
1. **User Input → Normalization → Storage**
   - Clean and validate user data before storing
   - Example: `normalize_song()` cleans title, artist, genre

2. **Profile-Based Classification**
   - User preferences affect how data is categorized
   - Example: `hype_min_energy` threshold determines playlist assignment

3. **Filter → Display Pattern**
   - Search queries filter data before rendering
   - Example: `search_songs()` → filtered list → display

4. **Random Selection with History**
   - Track user actions over time
   - Example: Lucky pick adds to history

### 7. Mermaid Diagrams
- Learned how to read flowchart syntax
- Understanding decision nodes (`{}`) vs process nodes (`[]`)
- Following data flow arrows between components

---

## Questions for Further Learning

- How does Streamlit's reactive model differ from traditional web frameworks?
- What are other ways to manage Python dependencies (Poetry, Pipenv)?
- How would I deploy this Streamlit app to production?
- What testing strategies work best for Streamlit apps?
- How can I optimize performance for larger datasets?

---

## Next Steps

- [ ] Experiment with modifying the classification logic
- [ ] Add new features (export playlists, import from CSV)
- [ ] Try creating a virtual environment from scratch
- [ ] Practice reading and creating control flow diagrams
- [ ] Learn about other Python environment managers (conda, poetry)
- [ ] Explore Streamlit's caching and performance features

---

**Session Date:** March 2, 2026  
**Project:** Playlist Chaos - AI-generated playlist engine
