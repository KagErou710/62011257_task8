<html>

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
        <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.1/dist/umd/popper.min.js" integrity="sha384-9/reFTGAW83EW2RDu2S0VKaIzap3H66lZH81PoYlFhbGU+6BZp6G7niu735Sk7lN" crossorigin="anonymous"></script>
        <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js" integrity="sha384-B4gt1jrGC7Jh4AgTPSdUtOBvfO8shuf57BaghqFfPlYxofvL8/KUEfYiJOMMV+rV" crossorigin="anonymous"></script>
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" integrity="sha384-JcKb8q3iqJ61gNV9KGb8thSsNjpSL0n8PARn9HuZOnIxN0hoP+VmmDGMN5t9UJ0Z" crossorigin="anonymous">
    
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
        
        
    </head>

    <script
    src="https://code.jquery.com/jquery-3.5.1.min.js"
    integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0="
    crossorigin="anonymous">
    </script>
    <div style="background-color:lightblue">
        <strong>Books search</strong>
        <br>
        <input type="text" value = "Innovation">
        <button onclick="search_click()">search</button>
    </div>
    <hr/>
    
    <ul id="list" class = "container"></ul>
    
    <script>
        function search_click() {
    $.ajax({
    url: "https://www.googleapis.com/books/v1/volumes?q=title:innovation",
    type: "GET",
    cache: false,
    success: function(json) {
        html_str = '<p>' + json.items.length + '    result found</p>'
        $('#list').append(html_str);
    for(var i=0; i<json.items.length; i++){
        html_str = '<div class="border border-dark row" style = "background-color:honeydew;">'
        	+ '<div class = "col"><span class="title">'+'Title : '+json.items[i].volumeInfo.title+ '</span>' 
            +'<br><br>'+'<span class="author">'+'Authour : '+json.items[i].volumeInfo.authors.join(', ')+ '</span>'
            +'<br><span class="ISBN">ISBN : '+json.items[i].volumeInfo.industryIdentifiers[0].identifier+ '</span>'
            +'<br><span class="price">price : '+json.items[i].saleInfo.listPrice.amount + json.items[i].saleInfo.listPrice.currencyCode+ '</span>'
            +'<br></div><div class="col"><img src="'+json.items[i].volumeInfo.imageLinks.smallThumbnail+ '"></div>'
            +'<br></div><div style="background-color:white;"><br><br></div>'

        $('#list').append(html_str);
      }
    }
  });
}
    </script>


</html>
