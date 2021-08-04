# Conversational bot

## Preamble

AI chat bots are every where today, isn't it?

So i thought why not to create my own using  `transformers` library.

NOTE! Make sure you have `torch` installed. It is super important, unless our model won't work.

## Coding

Firstly, let's install the `transformers` module using `pip`.

```Python
!pip install transformers
```
Now, lets import some objects.

```Python
from transformers import AutoModelWithLMHead, AutoTokenizer
import torch
```

And yeah, that's pretty much all you need.

Let's load our model(of course i am not gonna make my own, are you insane?)

You can choose a different one if you want, but i chose microsofts dialog gpt.

```Python
model = "microsoft/DialoGPT-large"

tokenizer = AutoTokenizer.from_pretrained(model)
model = AutoModelWithLMHead.from_pretrained(model)
```
That's pretty much it, all what's left is to write a function, that will generate answers and catch some exceptions.

PS. I also a 'forget topic' feature in case you want to talk on a different topic or if model starts generating some nonsense.

```Python
def talk(model, tokenizer) -> None:
    forget_topic = 1

    while True:
        user_input = input(">> User:")

        if user_input == "Let's change the topic":
            forget_topic = 1
            user_input = input(">> User:")

        # encode the new user input, add the eos_token and return a tensor in Pytorch
        new_user_input_ids = tokenizer.encode(user_input + tokenizer.eos_token, return_tensors='pt')

        # append the new user input tokens to the chat history
        bot_input_ids = torch.cat([chat_history_ids, new_user_input_ids], dim=-1) if forget_topic == 0 else new_user_input_ids

        forget_topic = 0

        try:
            # generated a response while limiting the total chat history to 200 tokens
            chat_history_ids = model.generate(bot_input_ids, max_length=200, pad_token_id=tokenizer.eos_token_id, )

            # pretty print last ouput tokens from bot
            print(">> Model: {}".format(tokenizer.decode(chat_history_ids[:, bot_input_ids.shape[-1]:][0], skip_special_tokens=True)))

        except:
            print('Try using different model')
```

That wraps it up for this project, now just run `talk(model, tokenizer)` and enjoy.

BTW, don't forget to star <3


