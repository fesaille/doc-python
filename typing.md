# Typing

## History

PEPS:

- **Literature Overview for Type Hints** <badge-pep nr='482'></badge-pep>
- **Theory of Type Hints** <badge-pep nr='483'></badge-pep>
- **Type Hints** <badge-pep nr='484'></badge-pep> <badge-stars repo='python/typing'></badge-stars>
- **TypedDict** <badge-pep nr='589'></badge-pep>
- **Protocols: Structural subtyping** <badge-pep nr='544'></badge-pep>

??? Info "Nominal/Structural subtyping"

    PEP 544 does not suppress nominal subtyping (explicit declaration of base
    classes), instead propose usage of protocol classes  (static duck typing).

    === "Nominal subtyping"

        ```python
            from collections.abc import Sized, Iterable, Iterator

            class Bucket(Sized, Iterable[int]):
                ...
                def __len__(self) -> int: ...
                def __iter__(self) -> Iterator[int]: ...
        ```

    === "Structural subtyping"

        ```python
            from collections.abc import Iterator, Iterable

            class Bucket:  # Note: no base classes
                ...
                def __len__(self) -> int: ...
                def __iter__(self) -> Iterator[int]: ...
        ```


## Generic concrete collections

Dict
List
Set
FrozenSet
DefaultDict
OrderedDict
ChainMap
Counter
Deque

IO
TextIO
BinaryIO
Pattern
Match
Text

### Abstract Base Class



    ClassVar
    ContextManager
    Counter
    DefaultDict
    Deque
    final
    Final
    Literal
    NewType
    NoReturn
    overload (note that older versions of typing only let you use overload in stubs)
    Protocol (except on Python 3.5.0)
    runtime (except on Python 3.5.0)
    Text
    Type
    TypedDict
    TYPE_CHECKING


## Static type checker

### pytype

Pytype <badge-stars repo='google/pytype'></badge-stars> <badge-doc
href='https://google.github.io/pytype'></badge-doc>, not an official google project, checks and infers types for your Python code - without requiring type annotations


Package providing:

- <b>pydantic</b> <badge-stars repo='samuelcolvin/pydantic'></badge-stars> <badge-doc
href="https://pydantic-docs.helpmanual.io/"></badge-doc>

Link: https://www.pythonsheets.com/notes/python-typing.html
