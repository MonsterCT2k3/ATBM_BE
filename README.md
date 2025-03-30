1. tạo db "atbm_db"
2. sửa file appsettings.json
   "ConnectionStrings": {
   "DefaultConnection": "server=localhost;database=atbm_db;user=root;password=password của bạn"
   },
3. chạy dòng : "dotnet ef database update"
4. test api: register:
   bên fe gọi api :
   response = requests.get("http://localhost:5000/api/get-public-key")
   key_data = response.json()

N = int(key_data["N"])
E = int(key_data["E"])
lấy khóa public
sau đó gọi api register :
response = requests.post("http://localhost:5000/api/register", json={
"Data": [encrypted_data],
"N": str(N)
})
