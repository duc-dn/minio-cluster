## MINIO
---
- Creating minio cluster
![Minio cluster with 3 container running](./images/Screenshot%20from%202023-03-14%2023-52-32.png)

```
minio2:
    image: minio/minio
    container_name: minio2
    volumes:
      - ./data2:/data
    ports:
      - "9002:9001"
    environment:
      MINIO_ACCESS_KEY: admin
      MINIO_SECRET_KEY: admin123456789
    networks:
      - minio-net
    command: server --console-address ":9001" http://minio1/data http://minio2/data
```
- command: server --console-address ":9001": expose port for minio UI in port 9001 in container minio. After, mapping port 9001 in container to 9002 in local
