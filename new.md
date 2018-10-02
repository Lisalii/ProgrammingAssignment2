makeCacheMatrix<-function(x=matrix()){
  invMatrix<-NULL
  
  setMatrix<-function(y){
    x<<-y
    invMatrix<<-NULL
  }
  
  getMatrix<-function()x
  setInverse<-function(inverse)invMatrix<<-inverse
  getInverse<-function()invMatrix
  #get the value of the invertible matrix
  list(setMatrix=setMatrix,getMatirx=getMatix,
       setInverse=setInverse, getInverse=getInverse)
  
}


cacheSolve<-function(x,...){
  
invMatrix<-x$getInverse()
if(!is.null(invMatrix)){
  message("Getting Cached Invertible Matrix")
  returen(invMatrix)
}
#retrive the inverse cached if the inverse has already been calculated and the matrix has not been changed

MatrixData<-x$getMatrix()
invMatrix<-solve(MatrixData,...)
x$setInverse(invMatrix)
return(invMatrix)
#computes the inverse of the special "matrix" returned by makeCacheMatrix
#use the solve function to inverse the original matrix data and retrun them

}