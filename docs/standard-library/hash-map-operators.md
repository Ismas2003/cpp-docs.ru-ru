---
title: Операторы &lt;hash_map&gt;
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: ed143349f3afc7a27ad565c1cc929c6ecb5f6ad8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375450"
---
# <a name="lthash_mapgt-operators"></a>Операторы &lt;hash_map&gt;

|||
|-|-|
|[оператора!](#op_neq)|[оператор! (мультикарта)](#op_neq_mm)|
|[оператора](#op_eq_eq)|[оператор (мультикарта)](#op_eq_eq_mm)|

## <a name="operator"></a><a name="op_neq"></a>оператора!

> [!NOTE]
> Этот элемент API устарел. Вместо него следует использовать [класс unordered_map](unordered-map-class.md).

Проверяет неравенство объекта hash_map слева от оператора и объекта hash_map справа от оператора.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*Левой*\
Объект типа `hash_map`.

*Правильно*\
Объект типа `hash_map`.

### <a name="return-value"></a>Возвращаемое значение

**true**, если объекты hash_map не равны; **false**, если объекты hash_map равны.

### <a name="remarks"></a>Remarks

Сравнение между объектами hash_map основывается на попарном сравнении их элементов. Два объекта hash_map равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.

Члены [<hash_map>](hash-map.md) и [<hash_set>](hash-set.md) заголовки в [stdext Namespace](stdext-namespace.md).

### <a name="example"></a>Пример

```cpp
// hash_map_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a>оператора

> [!NOTE]
> Этот элемент API устарел. Вместо него следует использовать [класс unordered_map](unordered-map-class.md).

Проверяет равенство объекта hash_map слева от оператора и объекта hash_map справа от оператора.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*Левой*\
Объект типа `hash_map`.

*Правильно*\
Объект типа `hash_map`.

### <a name="return-value"></a>Возвращаемое значение

**true**, если объект hash_map слева от оператора равен объекту hash_map справа от оператора; в противном случае **false**.

### <a name="remarks"></a>Remarks

Сравнение между объектами hash_map основывается на попарном сравнении их элементов. Два объекта hash_map равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.

### <a name="example"></a>Пример

```cpp
// hash_map_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 == hm2 )
      cout << "The hash_maps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator-hash_multimap"></a><a name="op_neq_mm"></a>оператор! ( hash_multimap)

> [!NOTE]
> Этот элемент API устарел. Вместо него следует использовать [unordered_multimap Class](unordered-multimap-class.md).

Проверяет неравенство объекта hash_multimap слева от оператора и объекта hash_multimap справа от оператора.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*Левой*\
Объект типа `hash_multimap`.

*Правильно*\
Объект типа `hash_multimap`.

### <a name="return-value"></a>Возвращаемое значение

**true**, если объекты hash_multimap не равны; **false**, если они равны.

### <a name="remarks"></a>Remarks

Сравнение между объектами hash_multimap основывается на попарном сравнении их элементов. Два объекта hash_multimap равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.

### <a name="example"></a>Пример

```cpp
// hash_multimap_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="operator--hash_multimap"></a><a name="op_eq_eq_mm"></a>оператор (hash_multimap)

> [!NOTE]
> Этот элемент API устарел. Вместо него следует использовать [unordered_multimap Class](unordered-multimap-class.md).

Проверяет равенство объекта hash_multimap слева от оператора и объекта hash_multimap справа от оператора.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*Левой*\
Объект типа `hash_multimap`.

*Правильно*\
Объект типа `hash_multimap`.

### <a name="return-value"></a>Возвращаемое значение

**true**, если объект hash_multimap слева от оператора равен объекту hash_multimap справа от оператора; в противном случае **false**.

### <a name="remarks"></a>Remarks

Сравнение между объектами hash_multimap основывается на попарном сравнении их элементов. Два объекта hash_multimap равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.

### <a name="example"></a>Пример

```cpp
// hash_multimap_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1, hm2, hm3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      hm1.insert(Int_Pair(i, i));
      hm2.insert(Int_Pair(i, i*i));
      hm3.insert(Int_Pair(i, i));
   }

   if ( hm1 == hm2 )
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="see-also"></a>См. также раздел

[<hash_map>](hash-map.md)
