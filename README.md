# Screenshot using Golang with clean architecture
This is a Golang project to take screenshots from URLs using the Pdfcrowd API and save the image data to a MySQL database. Before I start explaining this project, please.

# install the following packages 
<br />
<ol>
  
  <li> go get github.com/go-sql-driver/mysql </li>
  <li> go get github.com/labstack/echo </li>
  <li> go get -u github.com/spf13/viper </li>
  <li> go get github.com/pdfcrowd/pdfcrowd-go</li>
  </ol>
<br />

<p>First, let me talk about the solution architecture. The architecture used is clean architecture with dependency injection.<p>
<p>
  This architecture has 4 layers
  <ol>
    <li> models</li>
    <li> imagehandler </li>
    <li> middleware </li>
    <li> imagehttphandler </li>
    </ol>
<p>
  
# Model layer
<p> The model layer is responsible for creating structs for our models to be transferred to the database or for binding the request to them.<br/>
<br />
  
# imagehandler
<p>This layer contains the repositories as well as the business logic. It is divided into two folders: one called 'usecase,' which handles all the business logic, and the other called 'repository,' which handles database operations. </p>

# middleware
<p> This is to handle the CORS (Cross-Origin Resource Sharing) on the HTTP requests </p>

# imagehttphandler
<p> This is responsible for creating the HTTP requests. It takes a list of URLs, then starts to take screenshots of those URLs and save the images to the specified folder path, which will be added to the config.json file. </P>

<p><u><b>In this case, I am using three packages.</b></u></p>
<ol>
  <li> go get github.com/labstack/echo </li>
  <li> go get -u github.com/spf13/viper </li>
  <li> go get github.com/pdfcrowd/pdfcrowd-go </li>
</ol>
# echo
<p> Why Echo? Because it provides high performance, extensibility, and a minimalist approach for a Go web framework./p>
  <p> For more information, please check this URL: https://echo.labstack.com/. </p>
  
 # viber
 <p> This helps to read the values from the configuration file. For more information, please check this URL: https://github.com/spf13/viper. </p>
 
 # pdfcrowd
 <p> This API will help us take a URL and convert it to an image. Unfortunately, this service is not free; I am currently using a trial. </p>

<p> After the screenshot has been taken, I moved it to a shared folder path with a UUID to create a unique name for the image. Then, the image data, including the folder path and creation time, will be saved to the database. </p>
  
