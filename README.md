# Huffman-Coding

# Aim
To implement Huffman coding to compress the data using Python.

# Software Required
Anaconda - Python 3.7

# Algorithm:

Step1:
Get the input string.

Step2:
Create tree nodes.

Step3:
Main function to implement huffman coding.

Step4:
calculate frequency of occurence.

Step5:
print the characters and its huffmancode.

Program:
```
# expt-11-huffman coding

# Step 1: Get the input string
input_string = "Programming"

# Step 2: Calculate frequency of each character
frequency = {}

for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Step 3: Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]

# Step 4: Build Huffman Tree
while len(nodes) > 1:

    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]

    nodes.append(new_node)

# Final Huffman Tree
huffman_tree = nodes[0]

# Step 5: Generate Huffman Codes
huffman_codes = {}

def generate_codes(tree, code=""):

    if isinstance(tree[0], str):
        huffman_codes[tree[0]] = code if code else "0"

    else:
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)

# Step 6: Display Results
print("Input String:", input_string)
print("\nCharacter Frequency and Huffman Codes")
print("--------------------------------------")

for char, freq in frequency.items():
    print(char, "  Frequency:", freq,
          "  Huffman Code:", huffman_codes[char])

# Step 7: Encode the input string
encoded_string = "".join(huffman_codes[char] for char in input_string)

print("\nEncoded Huffman String:")
print(encoded_string)
```
# OUTPUT: 
<img width="272" height="205" alt="image" src="https://github.com/user-attachments/assets/c05db21c-311c-4714-a980-161437b8eb1b" />

# Result
Thus the huffman coding was implemented to compress the data using python programming.
