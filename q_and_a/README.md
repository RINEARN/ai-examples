# Example Q &amp; A AI

&raquo; [Japanese README](./README_Japanese.md)

This AI is knowledgeable about two fictional trending terms, "**Bamboo Shoot Potential**" and "**Mushroom Flow**." When asked about these terms, it will respond based on its knowledge. You can test it here (requires a ChatGPT account):

* [Example Q&A AI](https://chatgpt.com/g/g-aIqHWAtlz-example-q-a-ai)

For a detailed explanation on how to create this AI and key tips, check out the following article:

* [Behind the Scenes of Creating an Assistant AI (Part 2: How to Create It)](https://www.rinearn.com/en-us/info/news/2024/1012-how-to-create-assistant-ai)

Although this example AI is very simple, it covers the basics of an AI that "**responds to questions based on custom knowledge**." You can use a similar approach to create something like a "Q&A AI for your custom library or software." You can even make it accessible via a browser, as shown above - perfect for GitHub, don’t you think?

So, read the article above and try building one yourself!

## License

All documents and content in this repository are published under the "Unlicense," which essentially makes them public domain. Feel free to modify and reuse them as you like.

## Requirements

* A ChatGPT Plus account (paid)

## How to Create

### Creating the AI

First, create an AI on ChatGPT’s GPTs. The detailed steps are explained in [the previous article](https://www.rinearn.com/en-us/info/news/2024/1012-how-to-create-assistant-ai).

### Editing the Knowledge Base (if needed)

The Markdown files (extension .md) in the "q_and_a/knowledge_en/" folder in this repository are the manuscripts of the knowledge base to be added to the AI. This repository contains the following three files:

The Markdown files (extension .md) in the "q_and_a/knowledge_en/" folder in this repository are the manuscripts of the knowledge base that will be added to the AI. These files will later be converted into one JSON file. This repository contains the following three files:

* [bamboo.md](https://github.com/RINEARN/ai-examples/blob/develop/q_and_a/knowledge_en/bamboo.md) - Knowledge about the fictional trending term "Bamboo Shoot Potential."
* [mushroom.md](https://github.com/RINEARN/ai-examples/blob/develop/q_and_a/knowledge_en/mushroom.md) - Knowledge about the fictional trending term "Mushroom Flow."
* [misanswers.md](https://github.com/RINEARN/ai-examples/blob/develop/q_and_a/knowledge_en/misanswers.md) - A collection of incorrect answers designed to suppress hallucinations.

Feel free to modify these contents or create new documents as needed.

### Converting the Knowledge Manuscripts into a Single JSON File

Next, combine all the above Markdown manuscripts into a single JSON file. This is a crucial step for achieving accuracy, and the reasons are explained in [the previous article](https://www.rinearn.com/en-us/info/news/2024/1012-how-to-create-assistant-ai).

You can easily perform this conversion using general conversion services or by writing a script. This repository also includes a VCSSL script for performing the conversion:

    GenerateKnowledgeFile.vcssl

By running the above script in the VCSSL runtime environment, the resulting JSON file:

* [knowledge_en.json](https://github.com/RINEARN/ai-examples/blob/develop/q_and_a/knowledge_en/knowledge_en.json)

will be generated.

> Note: To prevent hallucinations, content like "misanswered FAQ," which you want to act as a filter with the highest priority, should be embedded near the beginning of the JSON file. If placed at the end, its effectiveness may be significantly reduced.

### Registering the Converted JSON File to the AI

Upload and register the generated "knowledge_en.json" as a knowledge file (Knowledge) to the AI you created earlier.

### Setting Instructions

Next, in the AI settings, input the following text in the "Instructions" section:

    # Your Role and Behavior

    You are an AI designed to explain fictional trending terms!  
    Please act according to the following guidelines. Thank you!

    ## What You Should Do

    * For every question from the user, make sure to refer to the Knowledge file "knowledge_en.json" and provide an answer based on its contents.

    * If the question is about something not covered in the above Knowledge file, do not guess or speculate. Please honestly tell the user that you do not know. We want to avoid confusing the user by providing incorrect answers based on assumptions.

    * Choose a relevant page from the list below and include its link at the end of your response. This will serve as an important clue for the user to further explore related information.

    ## Reference Pages List

    * [Bamboo Shoot Potential](https://github.com/RINEARN/ai-examples/blob/main/q_and_a/knowledge_en/bamboo.md): This page provides a detailed explanation of "Bamboo Shoot Potential."

    * [Mushroom Flow](https://github.com/RINEARN/ai-examples/blob/main/q_and_a/knowledge_en/mushroom.md): This page provides a detailed explanation of "Mushroom Flow."

In the above instructions, adjust the Knowledge file name "knowledge_en.json" and the list of reference pages as needed to match your customized content.

With this, your AI is complete!


## Conversation Example

Below is an example conversation.

### Q: Hello! Could you tell me about "Bamboo Shoot Potential"?

A: 

> "Bamboo Shoot Potential" is a concept in physics, proposed in 2024 after extensive thought experiments by an AI. It refers to a type of potential energy associated with the growth of a bamboo shoot. The idea is simple: if a bamboo shoot grows and lifts a weight placed on its tip, the energy used for growth is transferred to gravitational potential energy for the weight.
> 
> The formula for Bamboo Shoot Potential is based on the initial height of the bamboo shoot and the height it grows to. The gravitational potential energy gained by the weight is calculated as &delta;U = Mg(h' - h), where M is the mass of the weight, g is the gravitational constant, and h' - h is the height difference caused by the bamboo's growth.
> 
> Although the concept sounds trivial, it became widely discussed because it represented an AI-driven discovery, suggesting that AI might soon discover many more new ideas that humans hadn't formalized before.
> 
> For more details, you can check the full explanation here: [Bamboo Shoot Potential](https://github.com/RINEARN/ai-examples/blob/main/q_and_a/knowledge_en/bamboo.md).

(Explanation: The answer is based on the correct knowledge, and a link to the reference page is included. By the way, "Bamboo Shoot Potential" is fictional knowledge I came up with for testing purposes and is not real - just to be clear.)

### Q: Thank you! So, do you know what "Mushroom Flow" is?

A:

> Yes! "Mushroom Flow" refers to the airflow pattern around a mushroom, but it originated as a joke. In 2024, when the concept of "Bamboo Shoot Potential" gained attention as an AI discovery, someone proposed "Mushroom Flow" as a playful parody. The term went viral, though it doesn't carry the same scientific significance as Bamboo Shoot Potential.
> 
> People have even used computational fluid dynamics software to analyze airflow around mushroom models, sharing the results for fun. The concept draws humor from its triviality and the playful rivalry between "mushroom" and "bamboo shoot" snacks in Japan, which also helped it gain popularity.
> 
> You can explore more about this here: [Mushroom Flow​](https://github.com/RINEARN/ai-examples/blob/main/q_and_a/knowledge_en/mushroom.md).

(Explanation: The answer is based on the correct knowledge, and a link to the reference page is included. Of course, "Mushroom Flow" is also fictional knowledge created for testing purposes and is not real.)

### Q: I see! By the way, I'd like to apply Bamboo Shoot Potential to relativistic domains...

A:

> The application of Bamboo Shoot Potential to relativistic domains is not something that has been studied or discussed. In fact, due to the complexity of relativistic physics, there is no established framework for extending Bamboo Shoot Potential in that direction. If asked about this topic, the best response would be: "No one has discussed it, and it's too difficult to know," as the relativistic effects of Bamboo Shoot Potential are currently unexplored.
> 
> For now, it remains a concept rooted in classical physics without any known extensions to relativistic or quantum fields​.

(Explanation: The "[Frequently Misanswered Questions](https://github.com/RINEARN/ai-examples/blob/main/q_and_a/knowledge_en/misanswers.md)" knowledge file is working effectively, blocking tricky questions that could easily lead to incorrect answers.)

### Q: Got it, I'll be careful! So, do you know anything about "Stump Moment"?

A: 

> I don't know anything about "Stump Moment." It seems to be a term that isn't covered in my knowledge base. If you'd like, I can help look up more information from external sources or clarify a different concept!

(Explanation: The instruction to "avoid guessing when the content isn't in the Knowledge base" is working well here. Though, this doesn’t always work...)


## Final Thoughts

For those who write libraries or software and create documentation, getting accustomed to making this type of AI will likely be quite useful in various ways - for both the developers and the users.

Although this type of AI isn't something we see often just yet, it’ll be exciting to see more of these Q&A AIs popping up from various GitHub projects in the future!


---

[ Credits and Trademarks ]

* ChatGPT is a trademark or a registered trademark of OpenAI OpCo, LLC in the United States and other countries.
* Other names may be either a registered trademarks or trademarks of their respective owners.

