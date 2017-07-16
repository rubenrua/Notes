# GRAPHQL


## Links

* http://graphql.org
* https://www.howtographql.com/



## Tools


### Client

* https://facebook.github.io/relay/
* http://dev.apollodata.com/
* http://vulcanjs.org/

### Server

* http://graphql.org/graphql-js: JS reference
* http://graphene-python.org: Python
* http://sangria-graphql.org: Scala

### Other

* https://github.com/graphql/graphiql:
* https://www.graph.cool: SAAS

## Other

* introspection query
```
query IntrospectionQuery {
  __schema {
    queryType { name }
    mutationType { name }
    subscriptionType { name }
    types {
      ...FullType
    }
    directives {
      name
      description
      args {
        ...InputValue
      }
      onOperation
      onFragment
      onField
    }
  }
}

fragment FullType on __Type {
  kind
  name
  description
  fields(includeDeprecated: true) {
    name
    description
    args {
      ...InputValue
    }
    type {
      ...TypeRef
    }
    isDeprecated
    deprecationReason
  }
  inputFields {
    ...InputValue
  }
  interfaces {
    ...TypeRef
  }
  enumValues(includeDeprecated: true) {
    name
    description
    isDeprecated
    deprecationReason
  }
  possibleTypes {
    ...TypeRef
  }
}

fragment InputValue on __InputValue {
  name
  description
  type { ...TypeRef }
  defaultValue
}

fragment TypeRef on __Type {
  kind
  name
  ofType {
    kind
    name
    ofType {
      kind
      name
      ofType {
        kind
        name
      }
    }
  }
}
```

https://gist.github.com/craigbeck/b90915d49fda19d5b2b17ead14dcd6da