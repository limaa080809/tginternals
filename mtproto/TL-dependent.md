# TL-dependent
In certain cases, types may depend not only on other types (polymorphism), but also on the parameters of another type (dependent types). The TL language provides very limited support for this functionality: dependence is only allowed on a natural parameter whose type is designated using # (alias nat, but this is private -- TL doesn't currently support this synonym). Values of type # are serialized as 32-bit signed numbers from 0 to 2^31-1.
Suppose we want to use induction to define the types “one integer”, “two integers”, and “three integers”. We could try to define them as follows:
or as:
or as:
The first two variations lead to the same serialization. For example, (2 3 9):%triple and (2 (3 9)):%triple serialize as three 32-bit numbers: 2 3 9. The last variation better emphasizes the inductive version of the definition, but it uses boxed types. This is good from a theoretical perspective, but it leads to “superfluous” constructor names in serialization.
Therefore, we will write %Type-Ident to indicate the bare type that corresponds to the boxed type Type-Ident with a single constructor. If this constructor is named constructor, then according to the definition %Type-Ident = %constructor. Now we can write our definition like this:
If we now abstract n out of the name of the type name and make it like a parameter for a polymorphic (dependent, to be more exact) type, then something like the following can be written in a suitable functional language:
In the TL language, it looks like this:
The function S : # -> # and the constant O : # (it is 0) are the function for the next natural number (S n = n + 1) and the constant null. Therefore, the type # (alias nat) behaves as if it were defined in TL using the constructors
or, using syntax more typical of other functional languages,
Types of all defined combinators:
or
Note that in this case the constructor tnil does not depend on the parameter n, while tcons does.
In an analogous manner, it is possible to define a complete binary tree of height h with strings in the leaf nodes:
Or a random tree whose leaf nodes are all a distance of h from the root and whose nodes are all labeled with integers:
Another version:
Let us try to define a type Tuple X n whose values are n-tuples of type X values. In this way, Tuple will be simultaneously polymorphic and dependent:
In the familiar syntax of functional languages:
or, in TL syntax,
In the end we obtain terms for the following types:
or
The Tuple we just defined differs from the built-in Vector type. Specifically, the Vector type formally depends on a single argument (a type), but our Tuple depends on two (a type and a number):
The built-in Vector could be defined in terms of our Tuple using “summing across all n : #":
Nevertheless, our Tuple has its advantages. For example, we can define data types such as:
In any event, remember that during calculation of the matrix_10x10 combinator's number, all parentheses must be removed and the CRC32 of the string matrix_10x10 a:%Tuple %Tuple double 10 10 = Matrix_10x10 must be computed.
Moreover, we can define arbitrarily-sized matrices:
In this case using vector would result in storing the length of a row (m) in each row, e.g. n times.
Note that the serializations of values of type %Tuple X n and vector X (also known as %vector X and %Vector X) nearly match when n > 0: in both cases we obtain a single 32-bit number (equal to n-1 or n depending on the version) followed by the serializations of n objects of type X. (This is slightly untrue: values of type %Tuple X n can only be serialized if n is a constant or value known from one of the preceding fields of the enclosing entry; but then this n won't be serialized explicitly anywhere).
In view of the importance of the construction presented above, it is built into the TL language in the following manner. A substructure in the form of [ array-field-name ":" ] [ nat-ident "" ] "[" field-descr ... "]” may be used in the declaration of any combinator, where nat-ident* is the name of any previously encountered field of type # (if it is not explicitly indicated, the most recent is used). In abstract, this substructure is equivalent to:
For example, 10x10 matrices, vectors, and arbitrary matrices may be defined in the following way:
We have already encountered the last version as a “definition” of the “built-in type” Vector.
Of course, several fields, as complex as desired, may be within the repeating part. Furthermore, besides using n as a repeat counter, one may use expressions of the form (n+const) and (const+n), where const is a small nonnegative constant, which are shorthand for S (S ( ... (S n) ... )):
To calculate the CRC32 these expressions are converted to expressions of the form (const+X) without internal spaces. Additionally, the * in this case is not set off by spaces on the left and right.
Serialization of dependent types and polymorphic types is not a fundamental challenge: we have combinators with non-zero arity with Type values. For example, the type Tuple double 10 : Type serializes to 'Tuple' '%double' 10. Note that at present in practice there is virtually no need to serialize types, whether dependent or not.
Optional combinator parameters in TL must possess the following properties:
- Optional parameters must be precisely the combinator's first several arguments;
- The value of any optional parameter must be entirely determined by the combinator's result type.
For example, in cons {X:Type} hd:X tl:(list X) = list X the parameter X may be made optional, because it is located at the very beginning of the argument list and is unambiguously determined by the list X result type. Similarly, in tcons {X:Type} {n:#} hd:X tl:(%Tuple X n) = Tuple X (S n) the values of X and n are completely determined based on the Tuple X (S n) result type, therefore they made be made optional parameters.
It usually makes sense to move all of a constructor's arguments satisfying the second condition to the beginning of the list, arrange them in the order they appear in the result type's parameters, and make them optional. Given such an approach, the full version of a constructor is rarely needed -- only when we want to transmit the value of the polymorphic or dependent type as a value of type Object. In all other cases, the type of the expected value from the context is already known, which means that all optional parameters can be recovered during decomposition.
See also Optional combinator parameters and their values.
