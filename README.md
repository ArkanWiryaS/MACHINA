# Face Mask Detection App

Yo! Ini adalah aplikasi deteksi masker wajah yang kece abis! Dibuat pake Streamlit + YOLOv8 buat ngecek apakah orang udah pake masker dengan benar atau belum.

##  Tech Stack

- **Streamlit** - Framework web app yang gampang banget
- **YOLOv8 (Ultralytics)** - Model AI buat object detection
- **OpenCV** - Library computer vision
- **PyTorch** - Deep learning framework
- **PIL** - Image processing
- **streamlit-webrtc** - Buat webcam streaming
- **Matplotlib** - Plotting (meskipun ga kepake di UI)

## 📋 Requirements

Pastiin lu udah install semua dependencies ini:

```bash
streamlit
opencv-python
numpy
torch
pillow
streamlit-webrtc
matplotlib
ultralytics
```

## 🚀 Cara Install & Jalanin

1. **Clone atau download** project ini
2. **Install dependencies**:
   ```bash
   pip install streamlit opencv-python numpy torch pillow streamlit-webrtc matplotlib ultralytics
   ```
3. **Pastiin ada file model** `best.pt` di folder yang sama
4. **Jalanin aplikasi**:
   ```bash
   streamlit run app.py
   ```


## 🎯 Cara Pake

### Mode 1: Upload Image
1. Pilih "Upload Image" di sidebar
2. Upload foto (format: JPG, JPEG, PNG)
3. Tunggu prosesing
4. Liat hasil deteksi di sebelah kanan
5. Scroll ke bawah buat liat detail hasil

### Mode 2: Webcam Real-time
1. Pilih "Use Webcam" di sidebar
2. Klik "Start" buat mulai streaming
3. Allow akses kamera di browser
4. Langsung keliatan deteksi real-time!

## 🧠 Gimana Cara Kerjanya?

### Model Loading
- Pake YOLOv8 model yang udah di-train (`best.pt`)
- Ada fix khusus buat PyTorch 2.6+ compatibility
- Model di-cache pake `@st.cache_resource` biar loading cuma sekali

### Image Processing
- Convert format gambar (RGBA → RGB, Grayscale → RGB)
- Jalanin inference pake YOLO model
- Generate gambar hasil dengan bounding boxes
- Extract info deteksi (class, confidence score)

### Webcam Processing
- Pake `VideoProcessorBase` dari streamlit-webrtc
- Proses setiap frame secara real-time
- Ada error handling buat jaga-jaga kalau ada masalah

## 🎨 UI/UX Features

- **Custom CSS** dengan font Manrope yang kece
- **Sidebar biru** dengan styling yang smooth
- **Card layout** yang clean dan modern
- **Color coding**: 
  - 🟢 Hijau buat "with mask"
  - 🔴 Merah buat "without mask"
- **Responsive design** yang mobile-friendly

## 📊 Output yang Didapet

### Detection Results
- **Tabel hasil**: Class name + confidence score
- **Total detections**: Jumlah objek yang kedeteksi
- **Class counts**: Berapa banyak orang pake/ga pake masker
- **Visual feedback**: Warna hijau/merah buat indikator

### Real-time Stats
- Confidence level setiap deteksi
- Bounding boxes di gambar
- Live counting

## 🐛 Troubleshooting

### Model ga bisa load?
- Pastiin file `best.pt` ada dan ga corrupt
- Check PyTorch version (app udah ada compatibility fix)

### Webcam ga jalan?
- Allow camera access di browser
- Coba refresh page
- Check firewall/antivirus settings

### Error processing image?
- Coba format gambar lain (JPG recommended)
- Pastiin gambar ga terlalu gede
- Check internet connection

## 📁 File Structure

```
.
├── app.py          # Main application file
├── best.pt         # YOLOv8 trained model
└── README.md       # Documentation (ini file!)
```

## 🤖 Model Info

Model yang dipake udah di-train khusus buat deteksi masker dengan classes:
- `with_mask` - Orang yang pake masker
- `without_mask` - Orang yang ga pake masker
- `mask_weared_incorrect` - Masker dipake tapi salah (maybe)

## 🎯 Performance Tips

- **Image size**: Jangan upload gambar yang terlalu gede (resize dulu)
- **Webcam quality**: Lower resolution = faster processing
- **Browser**: Chrome/Firefox recommended buat webcam feature


### Customization:
- Ganti warna di CSS section
- Modify detection threshold di model inference
- Add more classes kalau mau detect objek lain

---

**Note**: Aplikasi ini dibuat buat educational/demo purposes. Buat production use, consider additional security measures dan optimisasi performance.

Enjoy detecting masks! 😷✨ 