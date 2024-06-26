---
description: "Learn more about interfaces for generic types in .NET."
title: Generic interfaces
titleSuffix: ""
ms.date: 07/25/2022
helpviewer_keywords: 
  - "generic interfaces [.NET]"
  - "equality comparisons [.NET]"
  - "generics [.NET], interfaces"
  - "ordering comparisons [.NET]"
---
# Generic interfaces in .NET

This article provides an overview of .NET's generic interfaces that provide common functionality across families of generic types.  
  
Generic interfaces provide type-safe counterparts to nongeneric interfaces for ordering and equality comparisons, and for functionality that's shared by generic collection types. .NET 7 introduces generic interfaces for number-like types, for example, <xref:System.Numerics.INumber%601?displayProperty=fullName>. These interfaces let you define generic methods that provide mathematical functionality, where the generic type parameter is constrained to be a type that implements a generic, numeric interface.
  
> [!NOTE]
> The type parameters of several generic interfaces are marked covariant or contravariant, providing greater flexibility in assigning and using types that implement these interfaces. For more information, see [Covariance and Contravariance](covariance-and-contravariance.md).  
  
## Equality and ordering comparisons  

- In the <xref:System> namespace, the **<xref:System.IComparable%601?displayProperty=nameWithType>** and **<xref:System.IEquatable%601?displayProperty=nameWithType>** generic interfaces, like their nongeneric counterparts, define methods for ordering comparisons and equality comparisons, respectively. Types implement these interfaces to provide the ability to perform such comparisons.  
  
- In the <xref:System.Collections.Generic> namespace, the **<xref:System.Collections.Generic.IComparer%601>** and **<xref:System.Collections.Generic.IEqualityComparer%601>** generic interfaces offer a way to define an ordering or equality comparison for types that don't implement the <xref:System.IComparable%601?displayProperty=nameWithType> or <xref:System.IEquatable%601?displayProperty=nameWithType> interface. They also provide a way to redefine those relationships for types that do.

  These interfaces are used by methods and constructors of many of the generic collection classes. For example, you can pass a generic <xref:System.Collections.Generic.IComparer%601> object to the constructor of the <xref:System.Collections.Generic.SortedDictionary%602> class to specify a sort order for a type that does not implement generic <xref:System.IComparable%601?displayProperty=nameWithType>. There are overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> generic static method and the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> instance method for sorting arrays and lists using generic <xref:System.Collections.Generic.IComparer%601> implementations.  
  
  The <xref:System.Collections.Generic.Comparer%601> and <xref:System.Collections.Generic.EqualityComparer%601> generic classes provide base classes for implementations of the <xref:System.Collections.Generic.IComparer%601> and <xref:System.Collections.Generic.IEqualityComparer%601> generic interfaces and also provide default ordering and equality comparisons through their respective <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> and <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> properties.  
  
## Collection functionality  

- The **<xref:System.Collections.Generic.ICollection%601>** generic interface is the basic interface for generic collection types. It provides basic functionality for adding, removing, copying, and enumerating elements. <xref:System.Collections.Generic.ICollection%601> inherits from both generic <xref:System.Collections.Generic.IEnumerable%601> and nongeneric <xref:System.Collections.IEnumerable>.  
  
- The **<xref:System.Collections.Generic.IList%601>** generic interface extends the <xref:System.Collections.Generic.ICollection%601> generic interface with methods for indexed retrieval.  
  
- The **<xref:System.Collections.Generic.IDictionary%602>** generic interface extends the <xref:System.Collections.Generic.ICollection%601> generic interface with methods for keyed retrieval. Generic dictionary types in the .NET base class library also implement the nongeneric <xref:System.Collections.IDictionary> interface.  
  
- The **<xref:System.Collections.Generic.IEnumerable%601>** generic interface provides a generic enumerator structure. The <xref:System.Collections.Generic.IEnumerator%601> generic interface implemented by generic enumerators inherits the nongeneric <xref:System.Collections.IEnumerator> interface; the <xref:System.Collections.IEnumerator.MoveNext%2A> and <xref:System.Collections.IEnumerator.Reset%2A> members, which do not depend on the type parameter `T`, appear only on the nongeneric interface. This means that any consumer of the nongeneric interface can also consume the generic interface.

## Mathematical functionality

.NET 7 introduces generic interfaces in the <xref:System.Numerics?displayProperty=fullName> namespace that describe number-like types and the functionality available to them. The 20 numeric types that the .NET base class library provides, for example, <xref:System.Int32> and <xref:System.Double>, have been updated to implement these interfaces. The most prominent of these interfaces is <xref:System.Numerics.INumber%601>, which roughly corresponds to a "real" number.

For more information about these interfaces, see [Generic math](math.md).
  
## See also

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Generics](index.md)
- [Generic collections in .NET](collections.md)
- [Generic delegates for manipulating arrays and lists](delegates-for-manipulating-arrays-and-lists.md)
- [Covariance and contravariance](covariance-and-contravariance.md)
