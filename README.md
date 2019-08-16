### kryo
---
https://github.com/EsotericSoftware/kryo

```java
import com.esotericsoftware.kryo.Kryo;
import com.esotericsoftware.kryo.io.Input;
import com.esotericsoftware.kryo.io.Output;
import java.io.*;

public class HelloKryo {
  static public void main (String[] args) throws Exception {
    Kryo kryo = new Kryo();
    kryo.register(SomeClass.class);
    
    SomeClass object = new SomeClass();
    object.value = "Hello Kryo!";
    
    Output output = new Output(new FileOutputStream("file.bin"));
    kryo.writeObject(output, object);
    output.close();
    
    Input input = new Input(new FileInputStream("file.bin"));
    SomeClass object2 = kryo.readObject(input, SomeClass.class);
    input.close();
  }
  static public class SomeClass {
    String value;
  }
}

OutputStream outputStram = new FileOutputStream("file.bin");
OutputChunked output = new OutputChunked(outputStream, 1024);
output.endChunks();
output.encChunks();
output.close();

InputStream outputStram = new FileInputStream("file.bin");
InputChunked input = new InputChunked(inputStream, 1024);
input.nextChunks();
input.nextChunks();
input.close();

kryo.writeClassAndObject(output, object);
Object object = kryo.readClassAndObject(input);
if (object instanceof SomeClass) {
}

kryo.writeObjectOrNull(output, object);
SomeClass object = kryo.readObjectOrNull(input, SomeClass.class);

kryo.writeObject(output, object);
SomeClass object = kryo.readObject(input, SomeClass.class);

Kryo kryo = new Kryo();
kryo.register(SomeClass.class);
SomeClass object1 = new SomeClass();
Output output = new Output(1024, -1);
kryo.writeObject(output, object);
Input input = new Input(output.getBuffer(), 0, output.position());
SomeClass object2 = kryo.readObject(input, SomeClass.class);


Kryo kryo = new Kryo();
SomeClass object = ...
SomeClass copy1 = kryo.copy(object);
SomeClass copy2 = kryo.copyShallow(object);

public boolean useReferences (Class type) {
  return !Util.isWrapperClass(type) && !Util.isEnum(type) && type != String.class;
}

static private final ThreadLocal<Kryo> kryos = new ThreadLocal<Kryo>() {
  protected Kryo initialValue() {
    return kryo;
  };
};
Kryo kryo = kryos.get();

Pool<Kryo> kryoPool = new Pool<Kryo>(true, false, 8) {
  protected Kryo create () {
    Kryo kryo = new Kryo();
    
    return kryo;
  }
};

Kryo kryo = kryoPool.obtain();
kryoPool.free(kryo);

Pool<Output> outputPool = new Pool<Output>(true, false, 16) {
  protected Output create () {
    return new Output(1024, -1);
  }
};
Output output = outputPool.obtain();
outputPool.free(output);

Pool<Input> inputPool = new Pool<Input>(true, false, 16) {
  protected Input create () {
    return new Input(1024, -1);
  }
};
Input input = inputPool.obtain();
inputPool.free(input);


Pool<Input> inputPool = new Pool<Input>(true, false, 16) {
  protected Input create () {
    return new Input(1024, -1);
  }
};
Input input = inputPool.obtain();
inputPool.free(input);
```

```
```

```
```
