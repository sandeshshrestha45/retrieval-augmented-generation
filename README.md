This is a RAG pipeline on gemma-2b-it model.

# What is RAG?
RAG stands for Retrieval Augmented Generation.

It was introduced in the paper Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks.

Each step can be roughly broken down to:

* Retrieval - Seeking relevant information from a source given a query. For example, getting relevant passages of Wikipedia text from a database given a question.
* Augmented - Using the relevant retrieved information to modify an input to a generative model (e.g. an LLM).
* Generation - Generating an output given an input. For example, in the case of an LLM, generating a passage of text given an input prompt.

### Why RAG?
The main goal of RAG is to improve the generation outptus of LLMs.

Two primary improvements can be seen as:

Preventing hallucinations - LLMs are incredible but they are prone to potential hallucination, as in, generating something that looks correct but isn't. RAG pipelines can help LLMs generate more factual outputs by providing them with factual (retrieved) inputs. And even if the generated answer from a RAG pipeline doesn't seem correct, because of retrieval, you also have access to the sources where it came from.
Work with custom data - Many base LLMs are trained with internet-scale text data. This means they have a great ability to model language, however, they often lack specific knowledge. RAG systems can provide LLMs with domain-specific data such as medical information or company documentation and thus customized their outputs to suit specific use cases.
The authors of the original RAG paper mentioned above outlined these two points in their discussion.

This work offers several positive societal benefits over previous work: the fact that it is more strongly grounded in real factual knowledge (in this case Wikipedia) makes it “hallucinate” less with generations that are more factual, and offers more control and interpretability. RAG could be employed in a wide variety of scenarios with direct benefit to society, for example by endowing it with a medical index and asking it open-domain questions on that topic, or by helping people be more effective at their jobs.

RAG can also be a much quicker solution to implement than fine-tuning an LLM on specific data.

What kind of problems can RAG be used for?
RAG can help anywhere there is a specific set of information that an LLM may not have in its training data (e.g. anything not publicly accessible on the internet).

For example you could use RAG for:

Customer support Q&A chat - By treating your existing customer support documentation as a resource, when a customer asks a question, you could have a system retrieve relevant documentation snippets and then have an LLM craft those snippets into an answer. Think of this as a "chatbot for your documentation". Klarna, a large financial company, uses a system like this to save $40M per year on customer support costs.
Email chain analysis - Let's say you're an insurance company with long threads of emails between customers and insurance agents. Instead of searching through each individual email, you could retrieve relevant passages and have an LLM create strucutred outputs of insurance claims.
Company internal documentation chat - If you've worked at a large company, you know how hard it can be to get an answer sometimes. Why not let a RAG system index your company information and have an LLM answer questions you may have? The benefit of RAG is that you will have references to resources to learn more if the LLM answer doesn't suffice.
Textbook Q&A - Let's say you're studying for your exams and constantly flicking through a large textbook looking for answers to your quesitons. RAG can help provide answers as well as references to learn more.
All of these have the common theme of retrieving relevant resources and then presenting them in an understandable way using an LLM.

From this angle, you can consider an LLM a calculator for words.

### Why local?
Privacy, speed, cost.

Running locally means you use your own hardware.

From a privacy standpoint, this means you don't have send potentially sensitive data to an API.

From a speed standpoint, it means you won't necessarily have to wait for an API queue or downtime, if your hardware is running, the pipeline can run.

And from a cost standpoint, running on your own hardware often has a heavier starting cost but little to no costs after that.

Performance wise, LLM APIs may still perform better than an open-source model running locally on general tasks but there are more and more examples appearing of smaller, focused models outperforming larger models.

 