R-programming-assignment-2
makeCacheMatrix <- function( x = matrix() ) {
  i <- NULL
  set <- function( matrix ) {
    x <<- matrix
    i <<- NULL
  }
  
  get <- function() {
    x
  }
  
  setInverse <- function(inverse) {
    i <<- inverse
  }

  getInverse <- function() {
    i
  }
  
  list(set = set, get = get,
       setInverse = setInverse,
       getInverse = getInverse)
}
cacheSolve <- function(z, ...) {
  
  x <- z$getInverse()
  
  if( !is.null(x) ) {
    message("getting cached data")
    return(x)
  }
  
  data <- z$get()
  
  x <- solve(data) %*% data
  
  z$setInverse(x)
  
  x
}

==========================
