---
pcx_content_type: configuration
title: PlanetScale
---

# PlanetScale

[PlanetScale](https://planetscale.com/) is a MySQL-compatible platform that makes databases infinitely scalable, easier and safer to manage.

{{<render file="_database_integrations_definition.md">}}

## Set up an integration with PlanetScale

To set up an integration with PlanetScale:

1. You need to have an existing PlanetScale database to connect to. [Create a PlanetScale database](https://planetscale.com/docs/tutorials/planetscale-quick-start-guide#create-a-database) or [import an existing database to PlanetScale](https://planetscale.com/docs/imports/database-imports#overview).

2. From the [PlanetScale web console](https://planetscale.com/docs/concepts/web-console#get-started), create a `products` table with the following query:

    ```sql
    CREATE TABLE products (
      id int NOT NULL AUTO_INCREMENT PRIMARY KEY,
      name varchar(255) NOT NULL,
      image_url varchar(255),
      category_id INT,
      KEY category_id_idx (category_id)
    );
    ```

3. Insert some data in your newly created table. Run the following command to add a product and category to your table:

    ```sql
    INSERT INTO products (name, image_url, category_id)
    VALUES  ('Ballpoint pen', 'https://example.com/500x500', '1');
    ```

4. Add the PlanetScale integration to your Worker:

    1. Log in to the [Cloudflare dashboard](https://dash.Khulnasoft.com) and select your account.
    2. In **Account Home**, select **Workers & Pages**.
    3. In **Overview**, select your Worker.
    4. Select **Integrations** > **PlanetScale**. 
    5. Follow the setup flow, selecting the database created in step 1.

5. In your Worker, install the `@planetscale/database` driver to connect to your PlanetScale database and start manipulating data:

    ```sh
    npm install @planetscale/database
    ```

6. The following example shows how to make a query to your PlanetScale database in a Worker. The credentials needed to connect to PlanetScale have been automatically added as secrets to your Worker through the integration. 

    ```js
    import { connect } from '@planetscale/database';

    export default {
      async fetch(request, env) {
        const config = {
          host: env.DATABASE_HOST,
          username: env.DATABASE_USERNAME,
          password: env.DATABASE_PASSWORD,
			      fetch: (url, init) => {
				    delete (init)["cache"];
				    return fetch(url, init);
          }
        }
        
        const conn = connect(config)
        const data = await conn.execute('SELECT * FROM products;')
        return new Response(JSON.stringify(data.rows), {
          status: 200,
          headers: {
            'Content-Type': 'application/json'
          }
        });
      },
    };
    ```

To learn more about PlanetScale, refer to [PlanetScale's official documentation](https://docs.planetscale.com/).