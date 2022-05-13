# how to prevent wp auto crop images while you upload

## STEP 1:
setting in wordpress interface

+ Login wp admin
+ Go to settings
+ Go to Media
+ Setting medium size and large to go 0
+ Click save

## STEP 2:
setting in theme codes
+ Find all folder of theme function add_image_size (/var/www/test/wp-content/themes/jnews)

+ in my case, i need to fix this function (
    Image.php
)
```
cd /var/www/test/wp-content/themes/jnews/class/Image/

vi Image.php
```

```php
 public function add_image_size()
    {
        # comment this function
        return;
        foreach($this->image_size as $id => $image)
        {
            add_image_size( $id, $image['width'], $image['height'], $image['crop'] );
        }
    }
```

+ comment code crop image in php code and save

+ try to upload image and view result