# Create-Knowledge-Graph-from-Large-text-file-using-chunking

Knowledge Graph :
A knowledge graph is a structured representation of information that connects entities and their relationships. It's essentially a semantic network where nodes represent entities (like people, places, things, or concepts) and edges represent the relationships between them (like "is_a", "has_part", "located_at").

Key characteristics of a knowledge graph:

Entities: The basic building blocks of a knowledge graph. They can be concrete objects (e.g., people, places, things) or abstract concepts (e.g., ideas, theories). Relationships: The connections between entities. They describe how entities are related to each other (e.g., "is_a", "has_part", "located_at"). Properties: Additional information associated with entities or relationships (e.g., attributes, values). How knowledge graphs are used:

Question Answering: Knowledge graphs can be used to answer complex questions by following the relationships between entities. Recommendation Systems: By analyzing the relationships between entities, knowledge graphs can recommend relevant items to users. Semantic Search: Knowledge graphs can improve search results by understanding the semantic meaning of queries and returning more relevant results. Data Integration: Knowledge graphs can be used to integrate data from multiple sources and provide a unified view of information. Examples of knowledge graphs:

Google Knowledge Graph: Used by Google Search to provide more informative and relevant search results.

DBpedia: A knowledge graph extracted from Wikipedia data.

Freebase: A large-scale knowledge graph developed by Google.

## Understanding the constraint with LLMs : 

Tokens are units of text that LLMs use to break down and analyze input. These tokens can represent individual words, sequences of characters, or combinations of words and punctuation. For example, the word "chatbot" would be treated as a single token. A sentence like "OpenAI is amazing!" might be split into multiple tokens depending on how the model processes it. Each large language model has a limit on the maximum number of tokens it can process in a single request.
![image](https://github.com/user-attachments/assets/b30e0754-3274-42bb-9ce9-7f77ec27fca8)

If we send an input prompt that is 5,000 tokens long, the model only has 3,192 tokens left for generating a response (because the sum of input + output cannot exceed the limit). If we don't account for the output token size, the model might truncate the response or not generate a response at all because the total token limit is exceeded. We can either shorten the input to leave enough room for a meaningful response or estimate the expected size of the response based on the nature of our prompt.

## Solution to the token limit : Chunking 

Chunking refers to splitting the input into smaller pieces. It works by:

a. Breaking the input text into smaller chunks, each fitting within the token limit.

b. Processing each chunk separately for entity and relationship extraction.

c. Combining the results from multiple chunks to form a complete knowledge graph.

![image](https://github.com/user-attachments/assets/7e73cb9b-965d-4b00-b166-0579e8efd734)

Implementation :

Step1 : Create the example folder structure with the respective files :

a. app.py : It is the executable file locally run through streamlit

b. entity_relationship_extraction.py : The logic for chunking , entity relationship extraction , which LLM to leverage and parsing llm response content

c. visualize_graph.py : It has the definition of how the knowledge graph should look like

d. raw_text.txt : This are sample .txt file which are used to create knowledge graph feel free to update with your specific .txt file and point to it .

Step 2 : Update the files

Update your OPEN AI Key and choice of model in entity_relationship_extraction.py . In model i considered "gpt-4o-mini" , you can update with your choice .

client = OpenAI(api_key="OPEN AI - API KEY")

response = client.chat.completions.create( model="gpt-4o-mini", messages=messages, )

Point to the .txt file of choice in app.py

text_file_path = "raw_text.txt"

Step 3 : run the requirements.txt file ( command : pip install -r requirements.txt )

Step 4 : run the streamlit app locally ( command : streamlit run app.py )

Visually you will see the following components :

Section 1 : It will highlight the extracted entities , a partial snapshot below .

![image](https://github.com/user-attachments/assets/efe4a391-ab68-494b-9edf-30288d6f849c)

Section 2 : It highlights the Extracted relationship tuples , a partial snapshot below .

![image](https://github.com/user-attachments/assets/395ebed3-9b4a-4fe7-a826-e0341981ca25)

Section 3 : Visualization of the knowledge graph .

![image](https://github.com/user-attachments/assets/d0e82a6d-9e2e-4b65-b8de-bd217231ca3c)

Happy coding :) 




