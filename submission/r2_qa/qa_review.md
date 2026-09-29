# QA review · B2-mid

Mã khóa: A0BD-01FD

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_060000.jpg | L1 | R03 | Box `Pedestrian` tách riêng người lái khỏi xe hai bánh nằm trong box `Bike` L4; theo R03, người lái và xe hai bánh phải được gán thành một box `Bike`. |
| adasind_102750.jpg | L1 | R04 | Đối tượng trong box L1 là một xe ba bánh/auto-rickshaw nhìn thấy trên ảnh, nhưng đang gán nhãn `Car`; theo R04 phải dùng `ThreeWheeler`. |
| adasind_102750.jpg | L2 | R04 | Đối tượng trong box L2 là một xe ba bánh/auto-rickshaw ở bên phải ảnh, nhưng đang gán nhãn `Bus`; theo R04 phải dùng `ThreeWheeler`. |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
