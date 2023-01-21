# EVA-8 Assignment3: Achieve 99.4% accuracy in less than or equal to 15 Epochs and 
Less than 10000 Parameters (additional points for doing this in less than 8000 pts). I have divided the task into 5 steps starting from basic setup to using things like dropout, batch normalisation, learning rate scheduler and image augmentation. I have created 5 notebooks one for each step. At the starting of each notebook, I have written the target, analysis and results.
Following are the targets, results and analysis we get from each step

## STEP-1
    **Target:**
    
        -- Get the set-up right
        -- Set Transforms
        -- Set Data Loader
        -- Set Basic Working Code
        -- Set Basic Training  & Test Loop
        -- Use batch normalisation 
    
    **Results:**
    
        -- Parameters: 6,383,818
        -- Best Training Accuracy: 99.99
        -- Best Test Accuracy: 99.61
    
    
    **Analysis:**
    
        -- The accuracy is really good. There is no overfitting as the test accuracy
        is increasing along with the training accuracy
        -- model is really heavy. 6.3M parameters are really heavy


## STEP-2
    **Target:**
    
        -- Our previous model has 6.3M parameters. I want to reduce these parameters here. I want to make them < 10K
    
    **Results:**
    
        -- Parameters: 9,907
        -- Best Training Accuracy: 99.99
        -- Best Test Accuracy: 99.05
    
    
    **Analysis:**
    
        -- The accuracy has dropped a little (from 99.61 to 99.05) after reducing the number of parameters
        -- traing and test accuracy are increasing with epochs. So we are in the right path. We might improve results by training it for few more epochs. We will keep number of epochs to 15 and increase it if required in future


## STEP-3
    **Target:**
    
        -- In the previous step we had 9,907 parameters. In this step we want to
        improve this accuracy by using dropouts. We will use a dropout rate of 0.05 
    
    **Results:**
    
        -- Parameters: 9,907
        -- Best Training Accuracy: 99.33
        -- Best Test Accuracy: 99.38
    
    
    **Analysis:**
    
        -- The accuracy has improved a little (from 99.05 to 99.38) after introducing dropouts.
        -- In some epochs, we can see that the training accuracy is increasing but the test accuracy is going up and down a little (which means the model is not able to find minima). 


## STEP-4
    **Target:**
    
        -- TO introduce accuracy we want the model to train on more difficult data. So we are introducing image augmentation in this step
    
    **Results:**
    
        -- Parameters: 9,907
        -- Best Training Accuracy: 99.08
        -- Best Test Accuracy: 99.35 (for one epoch it went to 99.4 but it might be a fluke. so we weill not consider that)
    
    
    **Analysis:**
    
        -- The accuracy has dropped a little (from 99.38 to 99.35) after introducing image augmentation.
        -- The training accuracy has gone down from 99.33 to 99.08. It is happening because, we are using doing image augmentation which means we are giving the model little more difficult data to train on 
        -- In some epochs, we can see that the training accuracy is increasing but the test accuracy is going up and down a little (which means the model is not able to find minima). 


## STEP-5
    **Target:**
    
        -- In the last step, we saw that the training accuracy is increasing but the test accuracy is going up and down a little (which means the model is not able to find minima). So, we want to introduce learning rate now
    
    **Results:**
    
        -- Parameters: 9,907
        -- Best Training Accuracy: 97.89
        -- Best Test Accuracy: 99.36
    
    
    **Analysis:**
    
        -- The accuracy has increased a little (from 99.31 to 99.36) after introducing learning rate scheduler.
        -- The training accuracy is same as previous step. 
        -- In the lest few epochs, the test accuracy is not introducing with increase in train accuracy. this means the model starts overfitting