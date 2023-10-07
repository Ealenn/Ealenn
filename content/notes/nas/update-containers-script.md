---
title: "NAS Update Containers Script"
weight: 1
---

{{< note title="NAS Update Containers Script" >}}
```sh
docker/
├─ update.sh
├─ project1/
│  ├─ docker-compose.yml
├─ project2/
│  ├─ docker-compose.yml
│  ├─ .DISABLED
```

---

```sh
#!/bin/bash
root_path="/volume1/docker"

###########################################
# UPDATE ALL PROJECTS
###########################################
# Use a for loop to iterate through folders in the directory
for folder in $root_path/*; do
  cd $root_path
  # Check if the item is a directory
  if [ -d "$folder" ]; then
    if [ -e "$folder/docker-compose.yml" ]; then
      echo "Docker project found in $folder"
      if [ -e "$folder/.DISABLED" ]; then
        echo "Project $folder was disabled. Skip."
      else
        echo "Project $folder enabled."
        cd $folder
        docker-compose pull
        docker-compose up -d
      fi
    else
      echo "Docker project not found in $folder"
    fi
  fi
done

###########################################
# CLEAN DOCKER IMAGES
###########################################
docker system prune --volumes -f
docker image prune -a -f
```
{{< /note >}}
