# PPTX Slide Title Extractor Docker Container
Docker container with Python script that extracts Slide Titles from a PPTX file

**Credit:**  
The Python script inside this container was authored by [Phill Moore](https://github.com/randomaccess3), he's really done all the hard work. I've just pulled this together into a Docker Container to try and make it quick and easy to use on any system.

---

## Prerequisites

1. **Install Docker Desktop**  
   Download and install Docker Desktop for your platform:  
   https://www.docker.com/products/docker-desktop

2. **Verify Docker**  
   ```bash docker --version```

## Pull Public Container from Docker Hub

_You only need to do this OR a Clone from GitHub, you don't need to do both._

1.  **Pull Container from Docker Hub**
    ```
    docker pull joshlemon/pptx-slide-title-extractor
    ```

## Clone Container from GitHub

_You only need to do this OR a Pull from Docker Hub, you don't need to do both._

1.  **Get the Repository**
    
    ```
    git clone https://github.com/joshlemon/pptx_slide_title_extraction_docker.git 
    cd Docker 
    ```

2. **Build the Docker Image**
   
   ``` docker build -t pptx-slide-title-extractor . ```


## Run the Container

1. **Run the Container**
   
   Example: scan current directory for PPTX files and write output.csv in the same dictory
   
   ``` 
   docker run --rm -v "$PWD":/data pptx-slide-title-extractor -d /data -o /data/output.csv
   ```

## Other Flags

- `-f /path/to/file.pptx`
Process a single PowerPoint file.

- `-d /path/to/directory`
Process all .pptx files in the directory.

- `-o /path/to/output.csv`
Path (inside or mounted) where the CSV results should be written. Defaults to output.csv in CWD

## Example Uasge

### Single file
```
docker run --rm -v "$PWD":/data pptx-slide-title-extractor -f /data/mydeck.pptx -o /data/mydeck_titles.csv
```

### Whole folder
```
docker run --rm -v "$PWD":/data pptx-slide-title-extractor -d /data/presentations -o /data/all_titles.csv
```

## To Do
- Add automated building and updates when/if Phil makes updates to the scipt so it's updated and pushed to Docker Hub
- Provide a Windows-specific usage example