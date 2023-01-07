Assignment for pytorch101

Assignment description: Take the image and a random number as input and predicted the image label and its sum with the random number as output.

layers Description: I have taken 3 convolutional layers and 3 fully connected layers:
    
    # Convolutional layers to process the image
    self.conv1 = nn.Conv2d(1, 32, kernel_size=3) --> conv layer with 32 kernels each with size 3*3
    self.conv2 = nn.Conv2d(32, 64, kernel_size=3) --> conv layer with 64 kernels each with size 3*3
    self.conv3 = nn.Conv2d(64, 128, kernel_size=3) --> conv layer with 128 kernels each with size 3*3   
    
    # Fully connected layers to process the image
    self.fc1 = nn.Linear(in_features=128, out_features=120) --> convert 128 features to 120 features
    self.fc2 = nn.Linear(in_features=120, out_features=60) --> convert 120 features to 60 features
    self.out = nn.Linear(in_features=60, out_features=10) --> convert 60 features to 10 features (as we have 10 classes)
    
How data goes through network:

    # after passing the batch through this network:
    we get the output as batch_size*10 (where 10 represents the number of classes -- "0 to 9")
    we then combine this output tensor batch_size*10 with the random number tensor to get a tensor batch_size*19 which represents the sum of the predicted label with the random number
    
    # we then calculate the loss using cross entropy as follows
    label_preds, sum_preds = network(images, random_nums) # Pass Batch to image and get output
    label_loss = F.cross_entropy(label_preds, labels) # calculate the loss for labels 
    sum_loss = F.cross_entropy(sum_preds, sums) # calculate the loss for sum
    loss = 0.5 * (label_loss + sum_loss) # Calculate total Loss by taking average
    
    # then we apply backpropragation and update weights
    optimizer.zero_grad()
    label_loss.backward() # Calculate Gradients
    optimizer.step() # Update Weights
    
    # we repeat the above steps to reduce the loss for 20 epochs. Following are the results:
<img width="1268" alt="Screenshot 2023-01-07 at 7 32 42 PM" src="https://user-images.githubusercontent.com/31219508/211154680-92e92670-d8b3-4ab5-8a14-aeb9ff0bbcc5.png">

    
