# Neural Network Modeling with Branching

### Data
It is static data from eDX about employees with their attrition. There are 27 features including Attrition. Select only 10 main features which impacts the output Attrition and Department.  

### Modeling
Using Tensorflow Keras Model create Neural Network Model with 2 shared layers and passing data from one layer to another. Then branch out a hidden layer and output layer for each output Attrition and Department. Use Softmax for Department as it has 3 categories and Sigmoid for Attrtion as it is binary.  

Here is the summary of the Model:  

<pre style="white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace">┏━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━┓
┃<span style="font-weight: bold"> Layer (type)        </span>┃<span style="font-weight: bold"> Output Shape      </span>┃<span style="font-weight: bold">    Param # </span>┃<span style="font-weight: bold"> Connected to      </span>┃
┡━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━┩
│ input_data          │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">16</span>)        │          <span style="color: #00af00; text-decoration-color: #00af00">0</span> │ -                 │
│ (<span style="color: #0087ff; text-decoration-color: #0087ff">InputLayer</span>)        │                   │            │                   │
├─────────────────────┼───────────────────┼────────────┼───────────────────┤
│ shared_layer1       │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">64</span>)        │      <span style="color: #00af00; text-decoration-color: #00af00">1,088</span> │ input_data[<span style="color: #00af00; text-decoration-color: #00af00">0</span>][<span style="color: #00af00; text-decoration-color: #00af00">0</span>]  │
│ (<span style="color: #0087ff; text-decoration-color: #0087ff">Dense</span>)             │                   │            │                   │
├─────────────────────┼───────────────────┼────────────┼───────────────────┤
│ shared_layer2       │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">64</span>)        │      <span style="color: #00af00; text-decoration-color: #00af00">4,160</span> │ shared_layer1[<span style="color: #00af00; text-decoration-color: #00af00">0</span>]… │
│ (<span style="color: #0087ff; text-decoration-color: #0087ff">Dense</span>)             │                   │            │                   │
├─────────────────────┼───────────────────┼────────────┼───────────────────┤
│ h_dept_layer        │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">32</span>)        │      <span style="color: #00af00; text-decoration-color: #00af00">2,080</span> │ shared_layer2[<span style="color: #00af00; text-decoration-color: #00af00">0</span>]… │
│ (<span style="color: #0087ff; text-decoration-color: #0087ff">Dense</span>)             │                   │            │                   │
├─────────────────────┼───────────────────┼────────────┼───────────────────┤
│ h_attr_layer        │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">32</span>)        │      <span style="color: #00af00; text-decoration-color: #00af00">2,080</span> │ shared_layer2[<span style="color: #00af00; text-decoration-color: #00af00">0</span>]… │
│ (<span style="color: #0087ff; text-decoration-color: #0087ff">Dense</span>)             │                   │            │                   │
├─────────────────────┼───────────────────┼────────────┼───────────────────┤
│ department (<span style="color: #0087ff; text-decoration-color: #0087ff">Dense</span>)  │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">3</span>)         │         <span style="color: #00af00; text-decoration-color: #00af00">99</span> │ h_dept_layer[<span style="color: #00af00; text-decoration-color: #00af00">0</span>][<span style="color: #00af00; text-decoration-color: #00af00">…</span> │
├─────────────────────┼───────────────────┼────────────┼───────────────────┤
│ attrition (<span style="color: #0087ff; text-decoration-color: #0087ff">Dense</span>)   │ (<span style="color: #00d7ff; text-decoration-color: #00d7ff">None</span>, <span style="color: #00af00; text-decoration-color: #00af00">1</span>)         │         <span style="color: #00af00; text-decoration-color: #00af00">33</span> │ h_attr_layer[<span style="color: #00af00; text-decoration-color: #00af00">0</span>][<span style="color: #00af00; text-decoration-color: #00af00">…</span> │
└─────────────────────┴───────────────────┴────────────┴───────────────────┘
</pre>

### Results
Based on the data we got better accuracy for Attrition than Department.

Department predictions accuracy: 0.513605  
Attrition predictions accuracy: 0.802721