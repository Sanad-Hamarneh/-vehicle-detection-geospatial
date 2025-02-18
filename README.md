# 🛻 **Vehicle Detection**

This project aims to develop an **object detection model** for identifying and localizing **vehicles** in **RGB orthophoto maps**. The objective is to use high-resolution aerial imagery to detect vehicles, convert their locations into **GPS coordinates**, and export the results into **KML** and **GeoJSON** formats for further geospatial analysis and visualization.

## 📌 Project Overview  
- **Data Preprocessing**: Process large high-resolution RGB orthophoto maps by splitting them into smaller tiles for efficient model training and inference.  
- **Object Detection**: Train a **YOLOv8 model** to detect vehicles in the tiles.  
- **Coordinate Transformation**: Convert pixel-based bounding box coordinates into real-world **GPS coordinates** using affine transformation.  
- **Data Export**: Output vehicle locations into **GeoJSON** and **KML** files for easy visualization and further analysis in tools like **QGIS**.

## 🛠️ Techniques Used  

### 🔹 Data Preprocessing  
- **Splitting the Map**: Divided a large **TIFF image** into smaller 640x640 pixel tiles to reduce computational burden while maintaining geospatial integrity.  
- **Coordinate Transformation**: Applied **affine transformation** to convert pixel coordinates to real-world coordinates based on the metadata associated with each tile.  
- **Dataset Preparation**: Labeled 253 images with vehicles in varying conditions, ensuring robust model training.  

### 🔹 Object Detection Model  
- **YOLOv8 Model**: Chose YOLOv8 for its **real-time object detection** capabilities, which balance speed and accuracy for high-resolution aerial imagery.  
- **Transfer Learning**: Fine-tuned a pre-trained YOLOv8 model using labeled data for vehicle detection in orthophoto maps.  
- **Bounding Box Detection**: The model detects vehicles and generates bounding boxes, which are later mapped to GPS coordinates using affine transformation.  

### 🔹 Post-Processing  
- **Non-Maximum Suppression (NMS)**: Applied NMS to remove redundant bounding boxes and improve detection accuracy.  
- **GPS Coordinates Conversion**: Converted detected vehicle locations from pixel coordinates to **longitude and latitude** for proper geospatial representation.  
- **Data Export**: Exported detected vehicle coordinates into **GeoJSON** and **KML** files for visualization in QGIS or other geospatial tools.

## ⚠️ Issues Encountered  
- **Large Map Size**: The large size of the TIFF map (22.14 GB) required efficient preprocessing techniques (e.g., tiling and overlap handling).  
- **Data Imbalance**: The dataset for vehicle detection contained varying numbers of vehicle instances, which required careful handling during training to avoid bias.  
- **Edge Detection**: Some vehicle detections near the edges of tiles were less accurate due to the overlap and tiling approach.
