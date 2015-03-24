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
        strider addUser
    
    docker run -d --name=strider \
        --link strider-mongo:mongo \
        --env="DB_URI=mongodb://mongo/strider" \
        --env="PLUGIN_BITBUCKET_HOSTNAME=http://you.site.com" \
        --publish 80:3000 \
        m00t/strider