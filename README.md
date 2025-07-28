# PathFinder Agent

Agentic AI application to evaluate candidate readiness for any target job title. The agent reads a candidate's resume and a target job title, then assesses the candidate’s readiness for the role. Built using OpenAI GPT models and LangChain, this project shows how agentic workflows can be used for intelligent matching in HR tech, learning & development, and career pathing.

Inputs:
1. A PDF resume or CV
2. Target job role - can include company and industry details for focused matching. e.g. "Sr. Data Scientist at Google"
3. An LLM API key - required to operationalize the agent
   
Outputs:
1. Readiness Score – A float value representing how well the resume matches the role
2. Missing Skills – A list of skills the candidate needs to acquire to be role-ready


Inner Wiring:
1. **Resume Parsing**: Extracts raw text from a PDF resume.
2. **Skill Extraction**: Uses GPT to extract up to 15 hard and 15 soft skills from the resume.
3. **Role Skill Inference**: Uses GPT to extract the most relevant hard and soft skills for a given job role/title.
4. **Skill Matching**:
   - Performs intelligent (non-keyword) matching of resume skills with role-required skills using GPT.
   - Calculates match percentages for both hard and soft skills.
   - Identifies missing skills from both categories.
5. **Readiness Scoring**: Computes a readiness score with a weighted formula (default: 70% hard, 30% soft).
6. **Recommendations**: Suggests skills to acquire for closing the gap.
7. **Agent Orchestration**: Nodes are orchestrated using a stateful graph that passes and updates information across stages.



Built With:
* Python and LangChain (for workflow)
* OpenAI GPT-3.5 (for reasoning)
* PyMuPDF (fitz) (for PDF parsing)
