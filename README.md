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
