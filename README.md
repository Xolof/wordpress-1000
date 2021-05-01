# Wordpress test

A Wordpress instance for an experiment.

Built from official [Wordpress Docker image](https://hub.docker.com/_/wordpress)

## Deploy

`docker-compose up -d`

## Add a quantity of blog posts

Copy script to container.
`docker cp -r ./create-posts-script <containerId>:/var/www/html`

Enter the wordpress container.

`docker exec -it <containername> bash`

Change $numPosts to desired number of posts to create.

Stand in `/var/www/html/create-posts-script`.

`php script.php`

Now a quantity of posts should be created.

## Remove blog posts

Enter the wordpress db container:
`docker exec -it <containername> bash`

Enter MySQL:
`mysql -uexampleuser -pexamplepass`

`delete from wp_posts where ID > 24;`

`delete from wp_postmeta where post_id > 24;`

The blog should now be empty.

