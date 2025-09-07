****
Windows - pip install pytest pip install pytest-mock
Mac, Linux - pip3 install pytest pip3 install pytest-mock

test_moduleName.py is the usual naming conviction for the name of the test python file.


Integrating Dotnet with pytest

```
dotnet new classlib -n SampleLib

SampleLib/
 ├── SampleLib.csproj
 ├── Class1.cs         (default file, you can delete/replace with your Sample.cs)
 ├── bin/
 │   └── Release/
 │       └── net8.0/
 │           └── SampleLib.dll   <-- 🔹 this is what Python needs
 └── obj/

cd SampleLib

2. Replace `Class1.cs` with your own `Sample.cs`:

namespace SampleLib
{
    public class Sample
    {
        public int Add(int a, int b)
        {
            return a + b;
        }

        public int Multiply(int a, int b)
        {
            return a * b;
        }
    }
}

dotnet build -c Release
Location of dll file will be -> SampleLib/bin/Release/net8.0/SampleLib.dll


import clr
import pytest

clr.AddReference(r"absolutePath")

from SampleLib import Sample

def test_get_sum():
    sample = Sample()
    assert sample.Add(10, 12) == 22

def test_get_multiply():
    sample = Sample()
    assert sample.Multiply(10, 12) == 120


pytest -v

```

```
pytest test_sample.py::test_get_sum -v
```

![Unit testing](./images/Pasted%20image%2020250907232213.png)
![Alt text](./images/Pasted%20image%2020250907232409.png)
