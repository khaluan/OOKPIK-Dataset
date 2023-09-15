# OOKPIK-Dataset

OOKPIK dataset consists of images and captions collected from news articles and fact-checking website used for detecting out-of-context use of image-caption pair. 


## Dataset statistics

Dataset consists of 545 samples in two categories: out-of-context caption pair (392 samples) and not out-of-context caption pair (153 samples). 

## File structure
```
    test_data.json: Contains image path and captions
    
    img
    |_ AFP Factcheck_0.png
    |_ AFP Factcheck_1.png
    ...
    |_ Snopes_57.png

```

## Data format:

The data is stored in JSON format with each sample stored as a dictionary in a single lines

File structures for each samples 

```
{	
    "img_local_path": <img_path>,
	"caption1": <caption1>,
	"caption1_modified": <caption1_modified>,
	"caption1_entities": <caption1_entities>,
	"caption2": <caption2>,
	"caption2_modified": <caption2_modified>,
	"caption2_entities": <caption2_entities>,
	"article_url": <article_url>,
	"label": 0/1,
	"maskrcnn_bboxes": [ [x1,y1,x2,y2], [x1,y1,x2,y2], ... ]
}

```

| Key   | Description                                                                      |
| -------- | ------------------------------------------------------------------------------|
| `img_local_path`    | Source path in dataset directory for the image                    | 
| `caption1`          | First caption associated with the image                 |
| `caption1_modified`          | Modified Caption1  after applying Spacy NER                 |
| `caption1_entities`          | List that consists of mapping between modified named entities in the caption1 with the corresponding hypernym                 |
| `caption2`           | Second caption associated with the image                       |
| `caption2_modified`           | Modified Caption2  after applying Spacy NER                        |
| `caption2_entities`          | List that consists of mapping between modified named entities in the caption2 with the corresponding hypernym                 |
| `article_url`       | Link to the website image and caption scraped from                           |
| `label`  | Class label whether the two captions are out-of-context with respect to the image (1=Out-of-Context, 0=Not-Out-of-Context )                         |
| `maskrcnn_bboxes`          | List of detected bounding boxes corresponding to the image. (x1,y1) refers to start vertex of the rectangle and (x2, y2) refers to end vertex of the rectangle                  |
