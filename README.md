# Redux

- Là 1 thư viện JS
- quy trình quản lý state

## Lý do dùng Redux

- chi tiết: d36-40 / reason.md
- xử lý Wrap hell / re-render k mong đợi khi dùng ContextAPI

## Redux workflow

- quy trình rõ ràng, khái niệm cụ thể - có vai trò cụ thể
- Khi làm luôn tuân thủ theo:

* các khái niệm
* bố cục dự án
* tư duy triển khai để set lại state

- nhược điểm:

* phức tạp hóa vấn đề vs dự án nhỏ (nhưng k ai dùng redux để giải quyết các vấn đề nhỏ)
* khi code cần quản lý rất nhiều file (các khái niệm bóc tách thành các file khác nhau - cần thêm 3,4 files)
  -> fix = redux toolkit

### Workflow

- https://redux.js.org/assets/images/ReduxDataFlowDiagram-49fa8c3968371d9ef6f2a1486bd40a26.gif

- UI: người dùng click
- Event handler: xử lý sự kiện click -> dispatch: bắn đi 1 action
- Store:

* (Có) Reducer: nhận state hiện tại + action => xử lý => state mới
* (Chứa) State: nhận & cập nhập state -> re-render UI

## Redux concepts:

- Store: Nơi lưu trữ state
- State: Dữ liệu (thường là Global)
- Action: 1 obj mô tả hành động từ UI, gồm:
+ action type: ~ CRUD (required)
+ action payload: dữ liệu mang theo (optional): phục vụ xử lý logic trong reducer
- Dispatch: bắn đi 1 action
- Reducer: nhận state hiện tại + action => xử lý => state mới

### Quy trình:

User click (UI) => Event handle => Dispatch action => Reducer nhận action + state hiện tại => trả ra state mới => Re-render UI

## Làm việc với redux:

1. Tạo init state
2. Tạo reducer: 
- giúp xử lý và trả ra state mới
- nhận vào: 
+ state
+ action.type: ~ CRUD
3. Tạo store: bằng createStore: 
Trả về 1 obj store có:
- getState(): trả ra state hiện tại
- dispatch(action): bắn 1 action đến reducer
- subscribe(listener): 
+ Đăng ký 1 hàm callback listener để bik khi nào reducer trả ra state mới -> re-render 
+ store.subscribe(render): khi state cập nhập sẽ gọi hàm render. Trả về hàm unsubscribe - gọi để dừng chính listener đó

- khi khởi tạo: createStore sẽ gọi reducer() để lấy initState
- khi store gọi dispatch sẽ gọi reducer