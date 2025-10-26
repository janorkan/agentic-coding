project-root/
├── planning/                               # Project planning, vision and structured task planning 
│   ├── vision.md                           # Goal, vision, architectural concept, requirements for this project
│   ├── future_backlog.md                   # Future user stroy backlog for further improvements
│   ├── sprint/                             # Iterative feature development based on basic concept
│   │   ├── sprint-01/                      # First iteration with issues and tasks
│   |   │   ├── ISSUE_101_XYZ.md            # First issue with user story, scope, acceptance criteria and requirements
│   |   │   ├── issue_102_XYZ.md            # Second issue with user story, scope, acceptance criteria and requirements
│   │   ├── sprint-02/                      # Second iteration with issues and tasks
│   |   │   ├── issue_201_XYZ.md            # First issue with user story, scope, acceptance criteria and requirements
│   └── └── ├── issue_202_XYZ.md            # Second issue with user story, scope, acceptance criteria and requirements
|
├── .claude/                                # Agent instruction folder
│   ├── commands/                           # Custom agent commands
│   |   ├── plan.md                         # Planning command for conceptual work in the planning/ folder only
│   |   ├── refactors.md                    # Request safe refactors for files, classes and methods
│   |   ├── test.md                         # Generate tests for code
│   |   ├── review.md                       # Run code review agent
│   |   ├── document.md                     # Update docs automatically
│   ├── templates/                          # Templates with structure to be used
│   |   ├── issue.md                        # Template for new issues
│   |   ├── vision.md                       # Template for the vision-file
│   |   ├── backlog.md                      # Template for the backlog
│   |   ├── folder_structure.md             # Template for the overall repo structure
│   ├── agents/                             # Custom agent folder
│   |   ├── agents_memory/                  # memory files for agents
│   |   ├── master_prompter.md              # Prompt enhancement agent
│   |   ├── doc_boy.md                      # Documentation helper for README.MD and additional code documentation 
│   |   ├── qa_tester.md                    # Runs pytest, summarizes failures
│   |   ├── scrum_master.md                 # Defines issues, make tas planning, check project management
│   |   ├── data_kepper.md                  # Maintains embeddings, clears stale data
│   |   └── release_bot.md                  # Builds, tests, and bumps versions
│   ├── workflows/
│   |   ├──code_generation.yaml             # Workflow for code generation tasks  
│   |   ├──test_cycle.yaml                  # Workflow for testing tasks    
│   ├── skills/                             # Custom skills for agents    
│   ├── mcp_servers.json                    # Storing MCP server configurations
│   └── settings.json                       # Specific settings for agent work
│
├── src/                                    # Standard source code folder
│   ├── agents/                             # Agent definition code
│   ├── tools/                              # Agent tools code
│   ├── workflows/                          # Agent workflow code
│   ├── protocols/                          # Specific protocol code
│   ├── core/                               # Core code
│   ├── frontend/                           # Frontend code
│   ├── infra/                              # Infrastructure code
│   └── api/                                # API code
│
├── data/                                   # Data folder
│   ├── raw/                                # Input data from sources
│   ├── database/                           # Database files and code
│   ├── output/                             # Output data
│   ├── memory/                             # Agents memory files
│   |   ├── embeddings/                     
│   |   ├── logs/
│   |   ├── state/
│   └── └── settings.json  
│ 
├── tests/                                  # Testing code folder
│   ├── src/                                # Testing folder for src/ folder with identical structure
│   ├── specs/                              
│   ├── regression/
│   └── benchmarks/
│  
├── ops/                                    #  For CI/CD pipelines, deployment configs, or GitHub Actions.
│  
├── configs/                                # Stores YAML/JSON configs for workflows, environment presets, ...
│  
├── research/                               # Folder for exploratory code, experiments, or AI-assisted planning transcripts.
│ 
├── docs/                                   # Additional documentation folder
│   ├── architecture/                              
│   ├── adr/
│   └── tutorials/
|
├── README.md                               # Project description and instruction file
├── CLAUDE.md                               # Coding agent instruction, how to work in this project
├── .env                                    # Secrets
├── .env.example                            # Secrets example file
└── requirements.txt                        # Requirements
