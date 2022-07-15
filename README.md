# Scope

## Learning Goals

- Explain scope in Java

## Introduction

We have seen several examples where new curly brace blocks can be defined, and
every time a new set of matching `{` and `}` is created, it defines a new scope.
This means that the variables that are defined inside that scope are only known
to that scope.

## Scope Walkthrough

Consider the following code:

```java
public class StudentGame { // <- first scope
    int classLevelVariable;
    public static void main(String[] args) { // <- second scope
        int methodLevelVariable;
        boolean flag = false;
        if (flag) { // <- third scope
            // do something when flag is true
            int numberWhenFlagIsTrue = 12;
        } // <- end of third scope
        else { // <- fourth scope
            // do something else when flag is false
            int numberWhenFlagIsFalse = 5;
        } // <- end of fourth scope
    } // <- end of second scope
} // <- end of first scope
```

As we discussed before, curly brace "blocks" can be contained inside each other
like Russian dolls, which is the case here:

- The first scope is the top level scope, which means nothing can be defined
  outside it for our program
- The second scope is inside the first scope, which means the second scope has
  access to all the variables defined in the first scope
- The third scope is inside the second scope, which means the third scope has
  access to all the variables defined in the second scope, including the ones
  defined in the first scope
- The fourth scope is also inside the second scope, which means the fourth scope
  has access to all the variables defined in the second scope, including the
  ones defined in the first scope
- The fourth scope is a peer of the third scope, which means they cannot see
  each other's variables. A scope can only see its variables and the variables
  of all the scopes inside it.

In our example, the variables `numberWhenFlagIsTrue` and `numberWhenFlagIsFalse`
are each contained within their respective part of the `if` statement, so they
are not accessible outside either the `if` or the `else`.
