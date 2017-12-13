# ajax_wordpress

-> simple-ajax-example.js

<pre>

jQuery(document).ready(function($) {
    $.ajax({
        url: ajaxurl
        data: {'action': 'example_ajax_request'},
        success:function(data) {
            // This outputs the result of the ajax request
            console.log(data);
        },
        error: function(error){
            console.log(error);
        }
    });  
              
});

</pre>

-> function.php

<pre>
        
function example_ajax_request() {
 
    // The $_REQUEST contains all the data sent via ajax
    if ( isset($_REQUEST) ) {
        echo json_encode("it's work");
    }
     
    // Always exit in functions echoing ajax content
   exit;
}
 
add_action( 'wp_ajax_example_ajax_request', 'example_ajax_request' );

</pre>

-> also in function.php

<pre>

// If you wanted to also use the function for non-logged in users (in a theme for example)
add_action( 'wp_ajax_nopriv_example_ajax_request', 'example_ajax_request' );
    
</pre>

-> wordpress ajaxurl is not defined - function.php

<pre>
    
    function example_ajax_enqueue() {
	// Enqueue javascript on the frontend.
	wp_enqueue_script(
		'example-ajax-script',
		get_template_directory_uri() . '/js/simple-ajax-example.js',
		array('jquery')
	);
	// The wp_localize_script allows us to output the ajax_url path for our script to use.
	wp_localize_script(
		'example-ajax-script',
		'example_ajax_obj',
		array( 'ajaxurl' => admin_url( 'admin-ajax.php' ) )
	);
}
add_action( 'wp_enqueue_scripts', 'example_ajax_enqueue' );

</pre>

source -> https://wptheming.com/2013/07/simple-ajax-example/

