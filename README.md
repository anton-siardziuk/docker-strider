Strider Docker image
====================

Deploy
------

    docker run --name strider-mongo-data mongo /bin/true
    
    docker run -d --name strider-mongo --volumes-from strider-mongo-data mongo
    
    docker run --rm -it \
        --link strider-mongo:mongo \
        --env="DB_URI=mongodb://mongo/strider" \
        m00t/strider \
        strider addUser -l your_email_here@gmail.com -a
    
    docker run -d \
        --link strider-mongo:mongo \
        --env="DB_URI=mongodb://mongo/strider" \
        --publish 3000:3000 \
        m00t/strider