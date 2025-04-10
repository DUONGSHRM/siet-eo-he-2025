import React, { useState, useEffect } from 'react';
import { MoveUpRight } from 'lucide-react';

export default function Home() {
  const calculateTimeLeft = () => {
    const difference = +new Date("2025-04-30") - +new Date();
    let timeLeft = {};
    if (difference > 0) {
      timeLeft = {
        days: Math.floor(difference / (1000 * 60 * 60 * 24)),
        hours: Math.floor((difference / (1000 * 60 * 60)) % 24),
        minutes: Math.floor((difference / 1000 / 60) % 60),
        seconds: Math.floor((difference / 1000) % 60),
      };
    }
    return timeLeft;
  };

  const [timeLeft, setTimeLeft] = useState(calculateTimeLeft());

  useEffect(() => {
    const timer = setTimeout(() => {
      setTimeLeft(calculateTimeLeft());
    }, 1000);
    return () => clearTimeout(timer);
  });

  const timerComponents = Object.keys(timeLeft).map((interval) => (
    <span key={interval}>
      {timeLeft[interval]} {interval}{" "}
    </span>
  ));

  return (
    <main className="bg-gradient-to-b from-pink-100 to-white min-h-screen py-12 px-4 md:px-12">
      <div className="max-w-5xl mx-auto grid gap-12">
        {/* Countdown Section */}
        <div className="text-center bg-white p-6 rounded-xl shadow">
          <h2 className="text-2xl font-bold mb-4">Ưu đãi kết thúc sau:</h2>
          <div className="text-3xl font-semibold">
            {timerComponents.length ? timerComponents : <span>Hết hạn</span>}
          </div>
        </div>

        {/* Buổi học chi tiết */}
        <div className="grid md:grid-cols-3 gap-6">
          <div className="bg-white p-6 rounded-xl shadow">
            <h3 className="text-xl font-semibold mb-2">Buổi 1: Kích hoạt hành trình siết eo</h3>
            <ul className="list-disc list-inside text-gray-700">
              <li>Đo chỉ số cơ thể và đặt mục tiêu cá nhân</li>
              <li>Làm quen với latex kit</li>
              <li>Gợi ý thực đơn và playlist tập nhẹ</li>
            </ul>
          </div>
          <div className="bg-white p-6 rounded-xl shadow">
            <h3 className="text-xl font-semibold mb-2">Buổi 2: Rèn kỷ luật – Định hình eo</h3>
            <ul className="list-disc list-inside text-gray-700">
              <li>Theo dõi tiến độ và điều chỉnh</li>
              <li>Siết nhẹ với latex an toàn</li>
              <li>Bài tập đốt mỡ tại nhà</li>
            </ul>
          </div>
          <div className="bg-white p-6 rounded-xl shadow">
            <h3 className="text-xl font-semibold mb-2">Buổi 3: Tối ưu vóc dáng & thói quen</h3>
            <ul className="list-disc list-inside text-gray-700">
              <li>Review kết quả & nhận quà</li>
              <li>Tư vấn cá nhân hóa giữ dáng</li>
              <li>Mix đồ đẹp cùng latex</li>
            </ul>
          </div>
        </div>

        {/* Testimonials */}
        <div className="grid gap-6">
          <h2 className="text-3xl font-bold">Khách Hàng Nói Gì?</h2>
          <div className="grid md:grid-cols-2 gap-4">
            <div className="bg-white p-4 rounded-xl shadow">
              <p>“Mới tuần đầu mà bụng đã gọn rõ luôn! Latex mặc dễ chịu, không bị khó thở. Em mê luôn playlist tập nhẹ mỗi sáng.”</p>
              <p className="mt-2 font-semibold">– Lan Anh, 31 tuổi</p>
            </div>
            <div className="bg-white p-4 rounded-xl shadow">
              <p>“Đi làm văn phòng cả ngày, nhờ chị Dương hướng dẫn mà biết cách siết nhẹ nhàng, không ép xác mà vẫn có eo.”</p>
              <p className="mt-2 font-semibold">– Thu Hương, HR Executive</p>
            </div>
          </div>
        </div>

        {/* Form */}
        <div className="bg-white p-6 rounded-xl shadow grid gap-4">
          <h2 className="text-3xl font-bold">Đăng ký ngay</h2>
          <p className="text-lg">Điền thông tin để giữ suất và nhận bộ latex kit</p>
          <form className="grid gap-4">
            <input type="text" placeholder="Họ và tên" className="border p-3 rounded-xl" />
            <input type="email" placeholder="Email" className="border p-3 rounded-xl" />
            <input type="tel" placeholder="Số điện thoại" className="border p-3 rounded-xl" />
            <button type="submit" className="bg-pink-500 hover:bg-pink-600 text-white py-4 text-lg rounded-2xl flex items-center justify-center gap-2">
              Gửi đăng ký <MoveUpRight />
            </button>
          </form>
        </div>

        {/* Call to action */}
        <div className="text-center">
          <h2 className="text-3xl font-bold mb-4">Sẵn sàng Siết Eo Không Stress?</h2>
          <p className="mb-6 text-lg">Đặt trước ngay hôm nay để nhận ưu đãi + bộ quà tặng giới hạn!</p>
        </div>
      </div>
    </main>
  );
}
