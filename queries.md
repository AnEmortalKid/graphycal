# queries

Query to get file names and blob text:
```
query($user:String!, $repoName:String!, $branchDirExpr:String!) {
  repository(owner:$user, name:$repoName)
  {
    name
    object(expression:$branchDirExpr)
    {
      ... on Tree {
        entries {
	  name
	  object {
	    ... on Blob {
	      text
	    }
	  }
	}
      }
    }
  }
}
```

Variables:
```
{ "user": "AnEmortalKid",
"repoName" : "graphycal",
"branchDirExpr": "master:subdir/"
}
```
