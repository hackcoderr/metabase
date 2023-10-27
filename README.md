# metabase

```
version: '3'

services:
  postgres:
    container_name: postgres-container
    image: postgres
    environment:
      POSTGRES_PASSWORD: postgres
      POSTGRES_DB: mydb
    ports:
      - "5432:5432"
    volumes:
      - postgres-data:/var/lib/postgresql/data
    networks:
      - metabase-net

  metabase:
    image: metabase/metabase
    ports:
      - "3000:3000"
    links:
      - postgres:postgres
    volumes:
      - metabase-data:/metabase-data
    networks:
      - metabase-net

networks:
  metabase-net:

volumes:
  postgres-data:
  metabase-data:
```
