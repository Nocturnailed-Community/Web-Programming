```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Bootstrap Demo</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.2/css/bootstrap.min.css" rel="stylesheet">
  </head>
  <body>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container-fluid">
          <a class="navbar-brand" href="#">Brand</a>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
              <li class="nav-item">
                <a class="nav-link active" aria-current="page" href="#">Home</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">Features</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">Pricing</a>
              </li>
              <li class="nav-item">
                <a class="nav-link disabled" aria-disabled="true">Disabled</a>
              </li>
            </ul>
          </div>
        </div>
    </nav>

    <div class="container mt-5">
      <div class="row">
        <div class="col-md-8">
          <h1 class="text-primary">Hello, Bootstrap World!</h1>
          <p class="lead">This is a demonstration of Bootstrap working properly.</p>
          
          <div class="alert alert-success" role="alert">
            <h4 class="alert-heading">Bootstrap is working!</h4>
            <p>If you can see this styled alert box, then Bootstrap CSS is loading correctly.</p>
          </div>

          <div class="card mt-4">
            <div class="card-header">
              <h5 class="mb-0">Test Card</h5>
            </div>
            <div class="card-body">
              <p class="card-text">This card component shows that Bootstrap styles are applied.</p>
              <a href="#" class="btn btn-primary">Primary Button</a>
              <a href="#" class="btn btn-success ms-2">Success Button</a>
            </div>
          </div>
        </div>
        
        <div class="col-md-4">
          <div class="bg-light p-4 rounded">
            <h5>Sidebar</h5>
            <ul class="list-unstyled">
              <li><a href="#" class="text-decoration-none">Link 1</a></li>
              <li><a href="#" class="text-decoration-none">Link 2</a></li>
              <li><a href="#" class="text-decoration-none">Link 3</a></li>
            </ul>
          </div>
        </div>
      </div>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.2/js/bootstrap.bundle.min.js"></script>
  </body>
</html>
```
