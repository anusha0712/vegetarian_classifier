# War & Peas : A Food Classifer for Vegetarian Diets 

You can access it directly at [War & Peas](https://anusha0712.github.io/vegetarian_classifier/)

As a vegetarian, everytime I want to go out to eat in a new place, I have to go over menus with a fine tooth comb and identify vegetarian options. Sure, some make it easier by tagging items with a 'veggie' icon, but the fanicer the place, the more obscure it gets and the more confusing the ingredients. 
This is a prototype for a classifer that can take menu items as input and output whether they are vegetarian or meat options and also a veggie score. I'm specifically only focusing on vegetarian for now - not vegan. 
The ultimate use-case for this work-in-progress project is to be able to receive a menu in the form of a link or for you to be able to look up a restaurant and get their most current menu classified with vegetarian options and score.


## How it was built

This classfier is hosted by HuggingFace Spaces and uses Gradio. 

I tested 5 most popular zero-shot text classifying models on HuggingFace. The one used in this project is the [MoritzLaurer/DeBERTa-v3-base-mnli-fever-anli](https://huggingface.co/MoritzLaurer/DeBERTa-v3-base-mnli-fever-anli) classifer with a success rate of 88%.  


## Questions
For questions please contact [Anusha Subramanian](mailto:as7500@columbia.edu)
