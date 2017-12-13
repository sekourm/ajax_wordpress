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
