1. Used MealDB Api to get a list of recipes per cuisine 
And then cleaned up the ingredients and recipes with string method and pandas and created a final string as [name]: description of items
Did the same with Spoonacular API because the output for MealsDB was too little. This is when I was planning to build classifer

Recipe dataset out --> not creating test set of Menu items
Downloaded pdf menus of restaurants in the michelin guide (arbitary repo of menus)
Used Chatgpt to parse out menu items and put them into a csv of name and description 
Now tagging them manually as veg or not

TESTING CLASSIFIERS

- Facebook BART model : https://huggingface.co/facebook/bart-large-mnli
    wrote gradio code to figure out how to upload csv to gradio for classification


    df = pd.read_csv(food_items)
    
    candidate_labels = ['vegetarian', 'not vegetarian']
    results = df['test_str'].apply(lambda row: classifier(row, candidate_labels)) # will give all the scores

    df["bart_classified"] = results.apply(lambda x: x['labels'][0]) # extracting the top score (might need to finetune output)

    # trying to get it to return csv

    output_filename = "/tmp/bart_classified.csv"
    df[['Title', 'Description', 'Manual','bart_classified']].to_csv(output_filename, index=False)
    return output_filename

    Had to reach gradio docs and then realized this returning csv thing is not a good idea. 
    Spent hours running things on gradio but it ran in MINUTES on Jupyter notebooks so because great to test multiple classifiers


- Using the 73% classifier MoritzLaurer/deberta-v3-base-zeroshot-v1.1-all-33

I'm wondering if this approach works better:

- Get a test_str input 
- break it into tokens
- pass it into NER for FOOD 
- make those food words go into classification.
- the minute you encounter a non-veg item --> break and it's non veg 

Additional changes:
- tested the top function with the categories "vegetarian" and "meat" 
- tested it with "plant based" and "meat"
- success rate became like 83% when i used veg and meat so going with those categories instead especially if i break them into tokens

running it with NER + classification was only 70% so not that great

- trying with NER + classification but with bins vegetarian, meat, seafood


THESE ARE THE MAX SUCCESS RATES OF CLASSIFYING METHODOLOGIES TRIED:
# try veg and non veg without ner - (73% was highest)
# try with veg and non veg ner items. 48%
# try with veg and meat with ner - 68%
# try veg and meat without ner - (88%) - USING THIS Now




NEXT STEPS:

