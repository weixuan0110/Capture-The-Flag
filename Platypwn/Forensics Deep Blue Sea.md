# Deep Blue Sea: Write-Up

Credit to RE:UN1ON Team (I just do half then they have done this!!)
**Flag:** `PP{f1L3_F0rm4t5_XXXXXXXXXXXXXXXXXXX}`  (Not the flag)

---

## Challenge Description

Legendary pirate Bluebeard has travelled far and wide over the Deep Blue Sea and has seen every corner of it. The crew’s legendary ship, the Blue Pearl, is just as legendary. As is Bluebeard’s famous cutlass, and parrot, and eyepatch, and so on. Almost as legendary is Bluebeard’s ancient treasure map, on which parts of the Sea are said to be marked with blots of crimson ink. There, Bluebeard has buried countless treasures over the years. But the biggest treasure can only be found if all other stashes are discovered. Then, the legend goes, the Depth of the Sea at their locations points to where Bluebeard’s most enormous treasure lies, buried beneath the waves of the Deep Blue Sea itself.

Or so they say. You, a renowned treasure hunter, have paid a lot for the soggy piece of parchment now lying in front of you. It smells of seaweed and rip-off. You decide that it’s time to slowly peel it open and see if the Sea has left over anything of Bluebeard’s notes.

---

## Solution Steps

### 1. Extract the Files
1. **Unzip the file** to reveal `treasure-map.ora`.
2. **Inspect the file type**: `.ora` is an OpenRaster image format.  
   - Use **Krita** to open the file and explore its contents.

3. Use the following command to extract the layers from the `.ora` file:
   ```bash
   binwalk -e treasure-map.ora
   ```

   The extraction creates a directory named `treasure-map.ora.extracted`, containing individual image layers.

---

### 2. Identify the Key Layers
- **Layer 0 (`layer0.png`)**: Contains dots marked with crimson ink.(it looks transparent, but have rgba hidden in the png)
- **Layer 1 (`layer1.png`)**: Contains encoded information in the blue channel.

---

### 3. Extract Red Dot Coordinates from `layer0.png`
Using the script below, extract the coordinates of pixels where the red channel value is greater than 0, and green and blue are both 0.

#### Code:
```python
from PIL import Image

def extract_red_dots(image):
    """
    Extract coordinates of red dots from an image (where R > 0 and G = B = 0).
    """
    red_dot_coords = []
    width, height = image.size
    pixels = image.load()
    
    for x in range(width):
        for y in range(height):
            r, g, b, _ = pixels[x, y]  # Assuming RGBA
            if r > 0 and g == 0 and b == 0:  # Red dot condition
                red_dot_coords.append((x, y))
    
    return red_dot_coords
```

---

### 4. Decode the Message from `layer1.png`
Using the red dot coordinates extracted from `layer0.png`, decode the message by reading the **blue channel values** at these coordinates.

#### Code:
```python
def decode_blue_channel_dynamically(red_dot_coords, layer1_image):
    """
    Dynamically decode the blue channel values at red dot coordinates in layer1, 
    ordered left-to-right, top-to-bottom.
    """
    # Sort coordinates: first by y (top-to-bottom), then by x (left-to-right)
    sorted_coords = sorted(red_dot_coords, key=lambda coord: (coord[1], coord[0]))

    # Access pixel values for the sorted coordinates in layer1
    layer1_pixels = layer1_image.load()
    blue_channel_values = [layer1_pixels[coord][2] for coord in sorted_coords]

    # Decode blue channel values to ASCII characters
    decoded_message = ''.join(chr(b) for b in blue_channel_values if 32 <= b <= 126)
    return decoded_message, sorted_coords
```

---

### 5. Combine Everything to Reveal the Message

#### Full Script:
```python
from PIL import Image

def extract_red_dots(image):
    red_dot_coords = []
    width, height = image.size
    pixels = image.load()
    
    for x in range(width):
        for y in range(height):
            r, g, b, _ = pixels[x, y]
            if r > 0 and g == 0 and b == 0:
                red_dot_coords.append((x, y))
    
    return red_dot_coords

def decode_blue_channel_dynamically(red_dot_coords, layer1_image):
    sorted_coords = sorted(red_dot_coords, key=lambda coord: (coord[1], coord[0]))
    layer1_pixels = layer1_image.load()
    blue_channel_values = [layer1_pixels[coord][2] for coord in sorted_coords]
    decoded_message = ''.join(chr(b) for b in blue_channel_values if 32 <= b <= 126)
    return decoded_message, sorted_coords

# File paths
layer0_path = "layer0.png"
layer1_path = "layer1.png"

try:
    layer0_image = Image.open(layer0_path).convert("RGBA")
    layer1_image = Image.open(layer1_path).convert("RGBA")

    red_dot_coords = extract_red_dots(layer0_image)
    decoded_message, sorted_coords = decode_blue_channel_dynamically(red_dot_coords, layer1_image)

    print("Decoded Message:", decoded_message)
    for coord, char in zip(sorted_coords, decoded_message):
        print(f"{coord}: '{char}'")
except Exception as e:
    print(f"Error: {e}")
```

---

### 6. Output

#### Decoded Message:
```
PP{f1L3_F0rm4t5_XXXXXXXXXXXXXXXXXXXX}(Not the flag)
```

#### Coordinate Mapping:
```plaintext
(132, 13): 'P'
(235, 26): 'P'
(317, 39): '{'
(441, 52): 'f'
(12, 66): '1'
(89, 79): 'L'
(199, 92): '3'
...
```

---

## Tools Used
- **Krita**: For inspecting `.ora` file contents.
- **Binwalk**: For extracting image layers.
- **Python (PIL)**: For processing images and extracting data.

---

## Flag
```
PP{f1L3_F0rm4t5_XXXXXXXXXXXXXXXXXXXX} (Not the flag)
```

---

## Acknowledgements
- **RE:UN1ON Team**: Original solution credit!!!!

