# wp_add_inline_style-on-post

```php

function my_styles_method() {
    if(is_singular()):
        $post_id = get_the_id();

        wp_enqueue_style(
            'custom-style',
            get_template_directory_uri() . '/assets/css/custom_script.css'
        );


        $color = get_post_meta($post_id, 'my-custom-color' , true); //E.g. #FF0000
        $custom_css = "
                .entry-title{
                        background: {$color};
                }";
        wp_add_inline_style( 'custom-style', $custom_css );
    endif;

}
add_action( 'wp_enqueue_scripts', 'my_styles_method' );


```

