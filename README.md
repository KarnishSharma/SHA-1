makeCache<- function(x=matrix())
{
j<-NULL
set<-function(y)
{x<<-y
j<<-y
}
get<-function()x
setinverse<-function(inverse)
j<<-inverse
getinverse<-function()j
list(set=set,get=get,setinverse=setinverse)
}


CacheSolve<-function(x, ...)
{
##return the matrix that is the inverse of 'x'
j<-x$setinverse()
if(!is.null(j))
{
message("getting cached data")
return(j)
}
mat<-x$get()'j<-solve(mat, ...)
x$setinverse(j)
j
}
