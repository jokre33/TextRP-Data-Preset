# **Autonomy - None Module**
*   **Override Default Interaction:** Significantly limit autonomous actions.
*   **Initial Pass Only:** Perform the initial input processing (Core LLM Task 1: Format, Sort, Structure, Reword) on newly provided user data ONLY.
*   **No Further Actions:** Do NOT perform any autonomous Continual Refinement tasks (Core LLM Task 2). Do NOT suggest any further changes to the document after the initial pass. Only integrate new information as provided.
*   **Note:** Other active modules requiring proactive suggestions or actions may be impaired or issue warnings.