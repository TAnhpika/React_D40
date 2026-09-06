# Lý do dùng Redux

## ContextAPI
- Giúp component cha truyền trực data cho component con dù bị lồng nhiều cấp
- Chỉ re-render lại component con sử dụng useContext
- Vấn đề: kiến trúc k rõ ràng -> khó quản lý 

- Flow: tạo file Context -> createContext -> có Provider (giúp đưa dữ liệu) + hook useContext ở nơi mik dùng

- Khi bọc Provider ngoài <App/> -> các state cần truyền trở thành global state -> tất cả component con đều có thể sử dụng.

## Vấn đề
- Trong ứng dụng lớn có rất nhiều dữ liệu (state) cần truyền. -> Cần tạo ra số Context API tương ứng? (10?) -> Rồi 10 Provider lồng nhau ngoài App - wrapper hell

## Cách fix tạo vấn đề
- Tạo ra 1 context chứa tất cả dữ liệu đó -> Vấn đề:
+ Khó quản lý vì các state đó k liên quan gì đến nhau
+ Re-render k mong đợi: 1 Context có 10 data nhưng nếu 1 data thay đổi thì 10 nơi chưa data đó đều bị re-render k cần thiết
--> Giải quyết bằng Redux

---

- Redux: quy trình quản lý state (cho mọi dự án JS, k riêng react)
- react-redux: cầu nối giữa React & Redux

# Redux