#EF 

Прочитать информацию с бд с помощью EF Core
1. Создать новый контроллер и прокинуть в него через конструктор `DbContext`:
![[Pasted image 20231015125413.png]]
2. Нажать "Добавить View" чтобы докинуть UI 
![[Pasted image 20231015125342.png]]

Опция "Create" и "Update":
1. Добавляем в контроллер новый `ActionResult`:
![[Pasted image 20231015135111.png]]
![[Pasted image 20231015141749.png]]

Опция "Delete"
![[Pasted image 20231015142853.png]]

Bulk Insert Operation
![[Pasted image 20231015145210.png]]

1. Делаем метод `Add` в цикле for напрямую к бд и после вызываем `SaveChanges`
2. Создаем список экземпляров, заполняем его в цикле for и далее используем метод `AddRange` чтобы добавить целый список

При добавлении больше 4-х элементов в бд, вызывается "Bulk Insert" операция

Bulk Remove Operation
![[Pasted image 20231015160147.png]]
