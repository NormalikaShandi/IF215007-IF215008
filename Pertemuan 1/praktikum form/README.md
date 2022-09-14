```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- Link CSS Bootstrap -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-0evHe/X+R7YkIZDRvuzKMRqM+OrBnVFBL6DOitfPri4tjfHxaWutUpFmBp4vmVor" crossorigin="anonymous">

    <title>Form Pendataan nilai UAS</title>

    <style>
        .data-uas {
            display: flex;
            flex-direction: row;
        }
        .form-pendataan-uas, .tabel-uas {
            display: flex;
            flex-direction: column;
            padding: 6px;
            margin: 6px;
            flex-grow: 1;
            border: solid black;
            border-radius: 6px;
        }
    </style>
</head>
    <body>
        <div class="data-uas">
            <div class="form-pendataan-uas">
                <h1>Form Pendataan Nilai UAS</h1>
                <input class="form-control mb-2" type="text" id="nama" placeholder="Nama">
                <input class="form-control mb-2" type="text" id="nilai" placeholder="Nilai">
                <button class="btn btn-primary" name="submit" id="submit">Masukkan Data!</button>
            </div>
        <div class="tabel-uas">
            <h1>Data uas</h1>
            <table class="table table-bordered me-5">
                <thead>
                    <tr>
                        <th>No</th>
                        <th>Nama</th>
                        <th>Nilai</th>
                    </tr>
                </thead>
                <tbody id="tabel-tbody">
                    <tr>
                                            
                    </tr>
                </tbody>
            </table>
        </div>
        </div>
        <script>
            function tampilkanData() {
                const dataTersimpan = localStorage.getItem("dataTersimpan");
                const dataTersimpanObjectArray = JSON.parse(dataTersimpan);
                console.log("data:", dataTersimpanObjectArray);
    
                const tabel = document.getElementById("tabel-tbody"); 
    
                let isiTabel = ``;
    
                dataTersimpanObjectArray.forEach(function(dataTersimpanObject, index) {
                    isiTabel += `
                        <tr>
                            <td>${index + 1}</td>
                            <td>${dataTersimpanObject.nama}</td>
                            <td>${dataTersimpanObject.nilai}</td>
                        </tr>
                    `;
                });
    
                tabel.innerHTML = isiTabel;
                
            }
            
            var inputNama = document.getElementById("nama");
            var inputNilai = document.getElementById("nilai");
            var inputSubmit = document.getElementById("submit");
    
            inputSubmit.onclick = function() {
                const nama = inputNama.value;
                const nilai = inputNilai.value;
                const pesan = `Data nilai dari ${nama}, telah dikirim !`;
                const data = {
                    nama,
                    nilai,
                };
                alert(pesan);
                console.log(data);
    
                const dataTersimpan = localStorage.getItem("dataTersimpan");
                const dataTersimpanObjectArray = JSON.parse(dataTersimpan) 

                if(dataTersimpan === null) {
                    localStorage.setItem("dataTersimpan", JSON.stringify([data]));
                } else {
                    dataTersimpanObjectArray.push(data);
                    localStorage.setItem("dataTersimpan", JSON.stringify(dataTersimpanObjectArray));
                }
    
                console.log("data tersimpan: ", dataTersimpan);
                console.log("data tersimpan object array: ", dataTersimpanObjectArray);
                tampilkanData();
            };
        </script> 
    </body>
</html>
```
