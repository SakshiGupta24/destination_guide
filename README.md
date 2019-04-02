# destination_guide
This web application give details about any city you want to visit.
<html>
  <head>
      <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.0/css/bootstrap.min.css">
	  <link href="https://fonts.googleapis.com/css?family=Satisfy" rel="stylesheet">
	  <link href="https://fonts.googleapis.com/css?family=ZCOOL+XiaoWei" rel="stylesheet">
      <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
      <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
      <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
     <style>
	 
body {
 background: #ecc6ec;
  background: linear-gradient(to right, rgb(51, 102, 153), rgb(238, 51, 255));
  
font-family: 'ZCOOL XiaoWei', serif;
}
div{
  display: flex;
  flex-direction: row;
      } 
  form{ display: flex;
  flex-direction: row;
  align-content: center;
      } 
    
      $cardBorderWidth: 3px;
    .gallery-container {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  position: relative;
  
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 10px;
}
h1,h2{
font-family: 'Satisfy', cursive;
}
    </style>
  <script>
    function getDetails(){
      const $galleryContainer = document.querySelector('.gallery-container');
			var search =document.getElementById("search").value;
			var xmlhttp= new XMLHttpRequest();
			var url="https://www.triposo.com/api/20181213/location.json?id="+search+"&account=BQ5LZD7B&token=3br838zx6b3i3giztp9vn7cpofv2eyvg";
			xmlhttp.open("GET", url, true);
			xmlhttp.send();
			xmlhttp.onreadystatechange=function(){
				if(this.readyState === 4 && this.status === 200 )
				{   var res=this.responseText;
					var jsres=JSON.parse(res);
                    console.log(jsres);
         var name_search=jsres.results[0].name;
         console.log(name_search);
         //document.getElementById("name").value=namer;
         $("#name").append(name_search);
         $("#paras").append(jsres.results[0].snippet);
		 
		 
        var image_link = jsres.results[0].images[0].source_url;
        var galleryItem = document.createElement('div');
      galleryItem.classList.add('gallery-item');
      galleryItem.innerHTML = `
        <img class="gallery-image" src="${image_link}" style="height:200px; width:200px; padding:20px; margin:20px;"  alt="gallery image"/>
      `
	   $galleryContainer.appendChild(galleryItem);
	 var image_link = jsres.results[0].images[4].source_url;
        var galleryItem = document.createElement('div');
      galleryItem.classList.add('gallery-item');
      galleryItem.innerHTML = `
        <img class="gallery-image" src="${image_link}" style="height:200px; width:200px; padding:20px; margin:20px;" alt="gallery image"/>
      `
     
      $galleryContainer.appendChild(galleryItem);
      var image_link = jsres.results[0].images[2].source_url;
        var galleryItem = document.createElement('div');
      galleryItem.classList.add('gallery-item');
      galleryItem.innerHTML = `
        <img class="gallery-image" src="${image_link}" style="height:200px; width:200px; padding:20px; margin:20px;" alt="gallery image"/>
      `
      $galleryContainer.appendChild(galleryItem);
      var image_link = jsres.results[0].images[3].source_url;
        var galleryItem = document.createElement('div');
      galleryItem.classList.add('gallery-item');
      galleryItem.innerHTML = `
        <img class="gallery-image" src="${image_link}" style="height:200px; width:200px; padding:20px; margin:20px;" alt="gallery image"/>
      `
      $galleryContainer.appendChild(galleryItem);
          
		  var image_link = jsres.results[0].images[5].source_url;
        var galleryItem = document.createElement('div');
      galleryItem.classList.add('gallery-item');
      galleryItem.innerHTML = `
        <img class="gallery-image" src="${image_link}" style="height:200px; width:200px; padding:20px; margin:20px;" alt="gallery image"/>
      `
      $galleryContainer.appendChild(galleryItem);
				}
      }
    }
</script>
</head>
<body>
   <center> <h1>Travel Guide</h1></center><br>
    <center> <h2>Everything you want to know</h2></center>
<form class="form-group col-sm-6">
      <input type="text"  id="search" class="col-sm-2 form-control " placeholder="Enter text like: Kanpur" />
      <button type="button" name="button" class="btn btn-primary" onclick="getDetails()"> Search  </button>
    </form><br>
   <h2 id="name"></h2>
    <br>
    <div class="gallery-container"></div><br>
    <div class="gallery-container"></div>
	<div class="gallery-container"></div>
    <div class="gallery-container"></div>
<center><h3 id="paras" class="justify-content"></h3></center>
</body>
</html>
