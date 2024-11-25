## Development and Deployment of a 'Chat with LLM' Application Using the Gradio Blocks Framework

## DEVELOPED BY: SREEVALSAN 
## REGISTER NUMBER:212223240158

### AIM:
To design and deploy a "Chat with LLM" application by leveraging the Gradio Blocks UI framework to create an interactive interface for seamless user interaction with a large language model.

### PROBLEM STATEMENT:
Design and deploy a "Chat with LLM" application using Gradio Blocks framework to provide users with an interactive interface that allows them to communicate with a large language model (LLM) for text generation.

### DESIGN STEPS:

#### STEP 1:
Load a pre-trained large language model (GPT-2) from Hugging Face.

#### STEP 2:
Define the function to generate responses based on user input.

#### STEP 3:
Set up the Gradio interface using the Blocks API.

#### STEP 4:
Configure the layout to accept user input and display the generated response.

#### STEP 5:
Launch the Gradio application for user interaction.

### PROGRAM:
```py
import gradio as gr
from transformers import pipeline

chat_model = pipeline("text-generation", model="gpt2", max_length=200)

def generate_response(user_query):
    try:
        response = chat_model(user_query, max_length=150, num_return_sequences=1)
        return response[0]['generated_text']
    except Exception as e:
        return f"Error: {str(e)}"

app_interface = gr.Interface(
    fn=generate_response,
    inputs=[
        gr.Textbox(label="Query", placeholder="Type here"),
        gr.Button("Generate")
    ],
    outputs=gr.Textbox(label="Response:", lines=10, interactive=False),
    title="Chat with LLM"
)

app_interface.launch()

```

### OUTPUT:
![image](https://github.com/user-attachments/assets/61916732-4eb4-4ad8-8939-46da549d3667)

### RESULT:
This application allows users to input a query, which is then processed by the GPT-2 model, generating a relevant response. The user interacts with the model through the Gradio interface, and the response is displayed in the output box.

