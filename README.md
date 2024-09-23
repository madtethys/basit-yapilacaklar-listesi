# Yapılacaklar Listesi

Bu proje, kullanıcıların görevlerini kolayca yönetebileceği bir yapılacaklar listesi uygulamasıdır. Görevler eklenebilir, tamamlanmış olarak işaretlenebilir ve istenirse silinebilir.

## Özellikler

- Yeni görevler ekleyebilme.
- Görevleri tamamlandığı zaman üstü çizili hale getirme.
- Görevleri listeden silme.
- Kullanıcı dostu, basit bir arayüz.

## Kullanım

1. Projeyi bir HTML dosyası olarak kaydedin ve tarayıcınızda açın.
2. "Yeni görev ekleyin" giriş alanına görev adı yazın ve "Ekle" butonuna tıklayın ya da Enter tuşuna basın.
3. Listede görünen her görevi tamamlanmış olarak işaretlemek için üstüne tıklayabilirsiniz.
4. Görevi silmek için, görev adının yanında bulunan "Sil" butonuna tıklayın.

## Dosyalar

- `index.html`: HTML ve JavaScript kodlarını içeren ana dosyadır.
- `stil.css`: Stil kodlarını içeren css dosyasıdır.

## Nasıl Çalışır?

- Kullanıcı, giriş alanına yeni bir görev yazar ve "Ekle" butonuna basar veya klavyeden `Enter` tuşuna basar.
- Girilen görev, yapılacaklar listesine eklenir ve görevle birlikte bir "Sil" butonu da oluşturulur.
- Kullanıcı görevlerin üstüne tıkladığında görev tamamlanmış sayılır ve üzeri çizilir. Tekrar tıklandığında görev tamamlanmamış duruma geri döner.
- "Sil" butonuna basıldığında görev listeden kaldırılır.

## Örnek

```html
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" type="text/css" href="./stil.css" />
    <title>Yapılacaklar Listesi</title>
</head>
<body>
    <h1>Yapılacaklar Listesi</h1>
    <div>
        <input type="text" id="taskInput" placeholder="Yeni görev ekleyin" onkeypress="handleKeyPress(event)">
        <button onclick="addTask()">Ekle</button>
    </div>
    <ul id="taskList"></ul>

    <script>
        function addTask() {
            const taskInput = document.getElementById("taskInput");
            const task = taskInput.value.trim();

            if (task === "") {
                alert("Lütfen bir görev girin.");
                return;
            }

            const li = document.createElement("li");

            li.textContent = task;
            li.onclick = function() {
                li.classList.toggle("completed");
            };

            const deleteBtn = document.createElement("button");
            deleteBtn.textContent = "Sil";
            deleteBtn.className = "delete-btn";
            deleteBtn.onclick = function(event) {
                event.stopPropagation();
                li.remove();
            };

            li.appendChild(deleteBtn);
            document.getElementById("taskList").appendChild(li);
            taskInput.value = "";
        }

        function handleKeyPress(event) {
            if (event.key === "Enter") {
                addTask();
            }
        }
    </script>
</body>
</html>
```

## Katkıda Bulunma

Her türlü katkı ve geri bildirim memnuniyetle karşılanır. Pull request gönderebilir ya da issue açabilirsiniz.

## Lisans

Bu proje [MIT Lisansı](LICENSE) altında lisanslanmıştır.
