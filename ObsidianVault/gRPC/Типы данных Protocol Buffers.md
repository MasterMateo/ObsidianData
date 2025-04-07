#gRPC 

 - Скалярные типы(int32,int64,float,double,bool,string,bytes, fixed и тд)
 - Enum
 - Для добавления других типов данных(Datetime, Empty - для того чтобы сделать void метод) нужно сделать импорт типов из "google/protobuf/..."
 - Если нужны Nullable типы нужно сделать импорт "google/protobuf/wrappers.proto"
 - **Any** - позволяет иметь поле с динамическим значением типов. Для добавление ипорт "google/protobuf/any.proto"
 - **OneOf** - позволяет создать поле со списком разрешенных типов значение(либо null либо string)