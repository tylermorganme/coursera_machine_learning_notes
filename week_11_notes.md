# Machine Learning Pipelines
- Break the problem into smaller machine learning tasks.
- e.g. optical character recognition can be broken down into: Image -> Text detection -> Character Segmentation -> Character Recognition
# Sliding Window Detection
- Slide an area over an image.
- At each iteration try to classify the area.

# Getting Lots of Data
- Make sure you have a low bias classifier before you start finding a bunch of data or it may be wasteful to use more data. Keep increasing the number of features/model until you have a low bias model.
- Sometimes you can create artificial data.
- You can create it from scratch (e.g. putting random text on random backgrounds with different distortions and fonts).
- You can add artificial distortions to an existing training set.
  - By using distortions you can use a single labeled data and expand it to be multiple labeled entries.
# Ceiling Analysis
- Check each component in a machine learning pipeline with an accurate data set.
- Check the accuracy of each step of the process and see where components are underperforming.
- You then look at the marginal difference between each step.
- This process gives you an idea of what the upside potential is for trying to optimize any component of the pipeline.
