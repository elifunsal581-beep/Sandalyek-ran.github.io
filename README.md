# Sandalyek-ran.github.io
Bugün Aysun Hocanın verdiği blog ödevimi paylaşcam
```html
<!DOCTYPE html>
<html lang="tr" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tarihin Dijital İzleri - Tarih Performans Görevi Blogu</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome İkonları -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; }
        .glass-card {
            background: rgba(15, 23, 42, 0.75);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(168, 85, 247, 0.2);
        }
        .neon-glow {
            box-shadow: 0 0 25px -5px rgba(168, 85, 247, 0.35);
        }
    </style>
</head>
<body class="bg-[#030014] text-slate-100 min-h-screen selection:bg-purple-500 selection:text-white">

    <!-- Üst Menü -->
    <nav class="sticky top-0 z-50 backdrop-blur-xl bg-[#030014]/85 border-b border-purple-500/20">
        <div class="max-w-6xl mx-auto px-4 py-3.5 flex justify-between items-center">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-2xl bg-gradient-to-tr from-purple-600 via-pink-500 to-cyan-400 flex items-center justify-center shadow-lg shadow-purple-500/40 animate-pulse">
                    <i class="fa-solid fa-feather-pointed text-white text-base"></i>
                </div>
                <div>
                    <h1 class="text-sm font-extrabold bg-gradient-to-r from-purple-400 via-pink-400 to-cyan-400 bg-clip-text text-transparent">Tarihin Dijital İzleri</h1>
                    <span class="text-xs text-purple-300 font-bold tracking-wide">Şaban Efe Ünsal (9-A)</span>
                </div>
            </div>
            <div class="flex items-center gap-3 z-50">
                <span id="adminStatus" class="text-xs text-emerald-400 font-semibold hidden px-3.5 py-1 bg-emerald-500/10 rounded-full border border-emerald-500/30 shadow-sm">⚡ Admin Aktif</span>
                <button id="adminBtn" type="button" class="px-4 py-1.5 text-xs font-bold bg-purple-950/80 hover:bg-purple-900 text-purple-200 border border-purple-500/50 rounded-xl transition-all shadow-md cursor-pointer">Admin Girişi</button>
            </div>
        </div>
    </nav>

    <!-- Özel Şifre Giriş Modalı -->
    <div id="adminModal" class="fixed inset-0 z-50 flex items-center justify-center bg-black/80 backdrop-blur-sm hidden">
        <div class="glass-card w-full max-w-sm p-6 rounded-3xl border border-purple-500/40 shadow-2xl space-y-4">
            <div class="flex justify-between items-center">
                <h3 class="text-sm font-bold text-white flex items-center gap-2"><i class="fa-solid fa-lock text-purple-400"></i> Yönetici Girişi</h3>
                <button onclick="closeAdminModal()" class="text-slate-400 hover:text-white text-xs"><i class="fa-solid fa-xmark text-base"></i></button>
            </div>
            <p class="text-xs text-slate-400">Lütfen yönetici şifresini giriniz</p>
            <input type="password" id="modalPasswordInput" onkeydown="if(event.key==='Enter') submitAdminPassword()" placeholder="Şifre" class="w-full bg-slate-900/90 border border-purple-500/40 rounded-xl px-4 py-2.5 text-xs text-slate-200 focus:outline-none focus:border-purple-500">
            <div id="modalError" class="text-xs text-rose-400 font-semibold hidden"></div>
            <div class="flex gap-2 pt-2">
                <button onclick="closeAdminModal()" class="flex-1 py-2 bg-slate-800 hover:bg-slate-700 text-xs text-slate-300 font-bold rounded-xl transition-all">İptal</button>
                <button onclick="submitAdminPassword()" class="flex-1 py-2 bg-purple-600 hover:bg-purple-500 text-xs text-white font-bold rounded-xl transition-all">Giriş Yap</button>
            </div>
        </div>
    </div>

    <!-- Özel Bilgi / Bildirim Kutusu (Alert yerine) -->
    <div id="customToast" class="fixed bottom-5 right-5 z-50 translate-y-20 opacity-0 transition-all duration-300 bg-slate-900/95 border border-purple-500/50 px-5 py-3 rounded-2xl shadow-2xl flex items-center gap-3">
        <i id="toastIcon" class="fa-solid fa-circle-check text-emerald-400 text-base"></i>
        <span id="toastMessage" class="text-xs text-slate-200 font-medium">İşlem başarılı!</span>
    </div>

    <!-- Ana İçerik Konteyneri -->
    <main class="max-w-5xl mx-auto px-4 py-10 space-y-12">

        <!-- Hero / Başlık Bölümü -->
        <header class="text-center space-y-4 py-8">
            <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-purple-500/10 border border-purple-500/30 text-purple-300 text-xs font-medium">
                <i class="fa-solid fa-graduation-cap"></i> Tarih Performans Görevi
            </div>
            <h2 class="text-3xl md:text-5xl font-black tracking-tight bg-gradient-to-r from-white via-purple-200 to-cyan-300 bg-clip-text text-transparent">
                Dijitalleşmenin Tarih Araştırma ve Yazım Süreçlerine Etkisi
            </h2>
            <p class="text-slate-400 max-w-2xl mx-auto text-sm md:text-base leading-relaxed">
                Geçmişin tozlu raflarından dijital arşivlere uzanan serüven: Akademik etik, nesnel ölçütler ve modern araştırma yöntemleri.
            </p>
        </header>

        <!-- Admin Paneli (Başlangıçta Gizli) -->
        <section id="adminPanelSection" class="hidden glass-card rounded-3xl p-6 border-2 border-purple-500/40 shadow-2xl space-y-4">
            <div class="flex justify-between items-center border-b border-purple-500/20 pb-3">
                <h3 class="text-base font-bold text-purple-300 flex items-center gap-2">
                    <i class="fa-solid fa-wand-magic-sparkles text-pink-400"></i> Admin İçerik Yönetim Paneli
                </h3>
                <span class="text-xs text-slate-400">Yönetici Modu Aktif</span>
            </div>
            <div class="space-y-3">
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1">Blog Başlığı Düzenle</label>
                    <input type="text" id="adminTitleInput" value="Dijitalleşmenin Tarih Araştırma ve Yazım Süreçlerine Etkisi" class="w-full bg-slate-900/80 border border-purple-500/30 rounded-xl px-4 py-2 text-sm text-slate-200 focus:outline-none focus:border-purple-500">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1">Ana Metin / İçerik Ekle veya Düzenle</label>
                    <textarea id="adminContentInput" rows="4" class="w-full bg-slate-900/80 border border-purple-500/30 rounded-xl px-4 py-2 text-sm text-slate-200 focus:outline-none focus:border-purple-500">Dijitalleşme, tarih araştırmalarında devrim yaratmıştır...</textarea>
                </div>
                <button onclick="saveAdminChanges()" class="w-full py-2.5 bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-500 hover:to-pink-500 text-white font-bold text-xs rounded-xl shadow-lg shadow-purple-600/30 transition-all cursor-pointer">Değişiklikleri Kaydet ve Yayınla</button>
            </div>
        </section>

        <!-- Blog İçeriği / Makale -->
        <article class="glass-card rounded-3xl p-6 md:p-10 space-y-10 shadow-xl neon-glow">
            
            <!-- Bölüm 1: Giriş ve Tarih Metodolojisinde Dijital Dönüşüm -->
            <div class="space-y-6 text-slate-300 leading-relaxed text-sm md:text-base">
                <div class="flex items-center justify-between border-b border-purple-500/20 pb-4">
                    <h3 id="displayTitle" class="text-2xl font-bold text-white border-l-4 border-purple-500 pl-4">1. Tarih Yazımında Dijital Dönüşüm ve Genel Ağ Kaynakları</h3>
                    <span class="text-xs text-purple-400 font-medium hidden sm:inline-block"><i class="fa-regular fa-clock"></i> Okuma Süresi: ~5 Dk</span>
                </div>
                <p id="displayContent">
                    Tarih disiplini, insanlığın geçmişteki deneyimlerini, toplumsal değişimlerini ve medeniyet mirasını bilimsel yöntemlerle inceleyerek günümüze ve geleceğe ışık tutan köklü bir bilim dalıdır. 21. yüzyılda yaşanan hızlı dijitalleşme süreci, tarihçilerin çalışma yöntemlerinde köklü bir paradigma değişimi yaratmıştır. Geleneksel fiziksel arşivlerin tozlu raflarından dijital veritabanlarına geçiş, dünyanın dört bir yanındaki birincil elden belgelere (fermanlar, gazeteler, diplomatik yazışmalar, haritalar) saniyeler içinde erişim imkânı tanımaktadır.
                </p>
                <p>
                    Genel ağ (internet) üzerinden yürütülen tarihsel araştırmalarda; <strong>Devlet Arşivleri Başkanlığı Dijital Arşiv Sistemi</strong>, <strong>Europeana</strong>, <strong>World Digital Library</strong> ve <strong>JSTOR / DergiPark</strong> gibi hakemli akademik veritabanları araştırmacılara devasa bir bilgi havuzu sunmaktadır. Ancak bu bilgi bolluğu beraberinde "bilgi kirliliği" ve "dezenformasyon" risklerini de getirmektedir.
                </p>

                <!-- Bilgi Kartları Grid -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4 my-6">
                    <div class="bg-purple-950/30 border border-purple-500/20 p-5 rounded-2xl space-y-2 hover:border-purple-500/50 transition-all">
                        <h4 class="font-bold text-purple-300 flex items-center gap-2"><i class="fa-solid fa-shield-halved text-cyan-400"></i> Kaynak Tenkidi</h4>
                        <p class="text-xs text-slate-400 leading-relaxed">Dijital ortamda ulaşılan her belgenin doğruluğu (iç ve dış tenkit) titizlikle süzgeçten geçirilmeli, yazarın kimliği ve belgenin tarihi teyit edilmelidir.</p>
                    </div>
                    <div class="bg-purple-950/30 border border-purple-500/20 p-5 rounded-2xl space-y-2 hover:border-purple-500/50 transition-all">
                        <h4 class="font-bold text-purple-300 flex items-center gap-2"><i class="fa-solid fa-book-bookmark text-pink-400"></i> Akademik Etik & Atıf</h4>
                        <p class="text-xs text-slate-400 leading-relaxed">İntihalden kaçınmak amacıyla başkasının fikir ve verileri Chicago veya APA standartlarına uygun biçimde dipnot ve kaynakça ile gösterilmelidir.</p>
                    </div>
                    <div class="bg-purple-950/30 border border-purple-500/20 p-5 rounded-2xl space-y-2 hover:border-purple-500/50 transition-all">
                        <h4 class="font-bold text-purple-300 flex items-center gap-2"><i class="fa-solid fa-database text-emerald-400"></i> Dijital Beşeri Bilimler</h4>
                        <p class="text-xs text-slate-400 leading-relaxed">Coğrafi Bilgi Sistemleri (CBS), yapay zekâ destekli el yazması okuma (OCR/HTR) ve büyük veri analizi tarih araştırmalarını derinleştirmektedir.</p>
                    </div>
                </div>
            </div>

            <!-- Bölüm 2: Karşılaştırmalı Analiz Tablosu -->
            <div class="space-y-4">
                <h3 class="text-2xl font-bold text-white border-l-4 border-pink-500 pl-4">2. Geleneksel ve Dijital Tarih Araştırmalarının Karşılaştırılması</h3>
                <p class="text-sm text-slate-300">Tarih metodolojisindeki değişimi daha net görebilmek için klasik yöntemler ile modern dijital araçların sunduğu olanakları karşılaştıralım:</p>
                
                <div class="overflow-x-auto rounded-2xl border border-purple-500/30">
                    <table class="w-full text-left border-collapse text-xs md:text-sm">
                        <thead>
                            <tr class="bg-purple-950/60 text-purple-200 border-b border-purple-500/30">
                                <th class="p-4 font-bold">Kriter</th>
                                <th class="p-4 font-bold">Geleneksel Yöntemler</th>
                                <th class="p-4 font-bold">Dijital Tarih Yöntemleri</th>
                            </tr>
                        </thead>
                        <tbody class="divide-y divide-purple-500/20 text-slate-300 bg-slate-900/40">
                            <tr class="hover:bg-purple-950/20">
                                <td class="p-4 font-semibold text-white">Belgeye Erişim</td>
                                <td class="p-4">Fiziksel seyahat, kütüphane ve arşiv izni gerektirir.</td>
                                <td class="p-4 text-cyan-300">7/24 uzaktan erişim ve anında dijital indirme imkânı.</td>
                            </tr>
                            <tr class="hover:bg-purple-950/20">
                                <td class="p-4 font-semibold text-white">Veri Tarama Hızı</td>
                                <td class="p-4">Sayfalarca indeks ve katalogların tek tek okunması.</td>
                                <td class="p-4 text-cyan-300">Anahtar kelime (OCR) ile saniyeler içinde tam metin tarama.</td>
                            </tr>
                            <tr class="hover:bg-purple-950/20">
                                <td class="p-4 font-semibold text-white">Belge Koruma</td>
                                <td class="p-4">Fiziksel yıpranma, nem ve yangın riski taşır.</td>
                                <td class="p-4 text-cyan-300">Bulut yedekleme ve yüksek çözünürlüklü dijitalleştirme.</td>
                            </tr>
                            <tr class="hover:bg-purple-950/20">
                                <td class="p-4 font-semibold text-white">Sunum ve Paylaşım</td>
                                <td class="p-4">Basılı kitaplar, makaleler ve akademik dergiler.</td>
                                <td class="p-4 text-cyan-300">Etkileşimli haritalar, dijital sergiler, bloglar ve podcastler.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Bölüm 3: Multimedya ve Dijital Arşiv Süreci -->
            <div class="space-y-4">
                <h3 class="text-2xl font-bold text-white border-l-4 border-cyan-500 pl-4">3. Dijital Arşivleme Süreci ve Akademik Standartlar</h3>
                <p class="text-sm md:text-base text-slate-300 leading-relaxed">
                    Günümüzde Osmanlı Arşivi belgelerinden antik dönem yazıtlarına kadar milyonlarca tarihi materyal yüksek çözünürlüklü tarayıcılarla dijital ortama aktarılmaktadır. Bu süreçte <strong>metaveri (üst veri)</strong> etiketlemesi yapılarak belgenin dönemi, dili, konusu ve fon kodu sisteme işlenir. Böylece öğrenciler ve akademisyenler, doğru anahtar kelimelerle güvenilir birincil kaynaklara doğrudan ulaşabilmektedir.
                </p>

                <!-- Görsel / Multimedya Alanı -->
                <div class="rounded-2xl overflow-hidden border border-purple-500/30 bg-slate-900/60 p-3">
                    <img src="https://placehold.co/900x380/0f172a/c084fc?text=Dijital+Tarih+Arsivleri+ve+Akademik+Veri+Analizi" alt="Tarihsel Dijital Arşiv" class="w-full h-64 object-cover rounded-xl opacity-90 hover:opacity-100 transition-opacity">
                    <div class="flex justify-between items-center mt-2 px-1">
                        <p class="text-xs text-slate-400 italic">Görsel 1: Uluslararası Dijital Arşiv Veritabanı ve Belge Tasnif Modeli</p>
                        <span class="text-[10px] text-purple-400 font-semibold">Kaynak: Dijital Beşeri Bilimler Enstitüsü</span>
                    </div>
                </div>
            </div>

            <!-- Akademik Kaynakça Bölümü -->
            <div class="border-t border-purple-500/20 pt-6 space-y-3 bg-slate-900/30 p-5 rounded-2xl">
                <h4 class="font-bold text-purple-300 text-sm flex items-center gap-2"><i class="fa-solid fa-graduation-cap"></i> Akademik Kaynakça</h4>
                <ul class="list-disc list-inside text-xs text-slate-400 space-y-2 leading-relaxed">
                    <li><strong>Carr, E. H.</strong> (2015). <em>Tarih Nedir?</em> (Çev. M. G. Gürtürk). İstanbul: İletişim Yayınları.</li>
                    <li><strong>Millî Eğitim Bakanlığı (MEB).</strong> (2025). <em>Ortaöğretim Tarih Dersi Öğretim Programı ve Performans Görevi Değerlendirme Kriterleri</em>. Ankara.</li>
                    <li><strong>Şimşek, A.</strong> (Ed.). (2021). <em>Dijital Tarih: Yeni Yaklaşımlar ve Yöntemler</em>. Ankara: Pegem Akademi Yayıncılık.</li>
                    <li><strong>T.C. Cumhurbaşkanlığı Devlet Arşivleri Başkanlığı.</strong> <em>Dijital Arşiv Sistemi Kullanım Kılavuzu</em>. Erişim Adresi: <span class="text-cyan-400 underline">devletarsivleri.gov.tr</span></li>
                </ul>
            </div>
        </article>

        <!-- Etkileşimli Tarih Quizi -->
        <section class="glass-card rounded-3xl p-6 md:p-8 space-y-6 shadow-xl border border-cyan-500/30">
            <div class="text-center space-y-2">
                <span class="text-xs text-cyan-400 font-bold uppercase tracking-wider">Bilgi Yarışması</span>
                <h3 class="text-2xl font-black text-white">Tarih ve Dijitalleşme Mini Quiz</h3>
                <p class="text-xs text-slate-400">Bilgilerini test et, doğru cevapları hemen gör!</p>
            </div>
            
            <div id="quizContainer" class="space-y-6">
                <!-- Soru 1 -->
                <div class="bg-slate-900/60 p-5 rounded-2xl border border-purple-500/20 space-y-3">
                    <p class="text-sm font-semibold text-white">1. Tarih araştırmalarında internet kaynakları kullanılırken aşağıdakilerden hangisine dikkat edilmelidir?</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-2 text-xs">
                        <button onclick="checkAnswer(this, false, 1)" class="p-3 rounded-xl bg-purple-950/40 hover:bg-purple-900/60 border border-purple-500/30 text-left transition-all">A) Sadece popüler sosyal medya paylaşımlarına güvenilmelidir.</button>
                        <button onclick="checkAnswer(this, true, 1)" class="p-3 rounded-xl bg-purple-950/40 hover:bg-purple-900/60 border border-purple-500/30 text-left transition-all">B) Güvenilir akademik veritabanları ve kütüphane kaynakları taranmalıdır.</button>
                    </div>
                    <div id="feedback-1" class="text-xs font-semibold hidden"></div>
                </div>

                <!-- Soru 2 -->
                <div class="bg-slate-900/60 p-5 rounded-2xl border border-purple-500/20 space-y-3">
                    <p class="text-sm font-semibold text-white">2. Başkalarının fikirleri ve çalışmaları kullanılırken neye uyulmalıdır?</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-2 text-xs">
                        <button onclick="checkAnswer(this, true, 2)" class="p-3 rounded-xl bg-purple-950/40 hover:bg-purple-900/60 border border-purple-500/30 text-left transition-all">A) Bilimsel etik kurallarına ve atıf/kaynakça kurallarına.</button>
                        <button onclick="checkAnswer(this, false, 2)" class="p-3 rounded-xl bg-purple-950/40 hover:bg-purple-900/60 border border-purple-500/30 text-left transition-all">B) Kaynak göstermeden doğrudan metne eklenmelidir.</button>
                    </div>
                    <div id="feedback-2" class="text-xs font-semibold hidden"></div>
                </div>
            </div>
        </section>

        <!-- Sadece Adminin Kontrol Edebileceği Özel Anket Kısmı -->
        <section class="glass-card rounded-3xl p-6 md:p-8 space-y-6 shadow-xl border border-pink-500/30">
            <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
                <div>
                    <div class="flex items-center gap-2">
                        <span class="text-xs text-pink-400 font-bold uppercase tracking-wider"><i class="fa-solid fa-square-poll-vertical"></i> Sadece Admin Kontrolünde Anket</span>
                        <span id="pollStatusBadge" class="text-[10px] font-bold px-2 py-0.5 rounded-full bg-emerald-500/20 text-emerald-400 border border-emerald-500/30">Oylama Açık</span>
                    </div>
                    <h3 id="pollQuestionTitle" class="text-xl font-black text-white mt-1">Sizce dijital arşivler tarih araştırmalarını ne kadar kolaylaştırdı?</h3>
                </div>
                <!-- Admin Özel Anket Yönetim Butonları -->
                <div id="adminPollControls" class="hidden flex flex-wrap gap-2">
                    <button id="togglePollVotingBtn" onclick="togglePollVoting()" class="px-3 py-1.5 bg-amber-600 hover:bg-amber-500 text-white font-bold text-xs rounded-xl transition-all cursor-pointer"><i class="fa-solid fa-pause"></i> Oylamayı Durdur</button>
                    <button onclick="openNewPollModal()" class="px-3 py-1.5 bg-pink-600 hover:bg-pink-500 text-white font-bold text-xs rounded-xl transition-all cursor-pointer"><i class="fa-solid fa-plus"></i> Yeni Anket Aç</button>
                    <button onclick="resetPollVotes()" class="px-3 py-1.5 bg-rose-600 hover:bg-rose-500 text-white font-bold text-xs rounded-xl transition-all cursor-pointer"><i class="fa-solid fa-rotate-right"></i> Oyları Sıfırla</button>
                </div>
            </div>

            <div id="pollOptionsContainer" class="space-y-3">
                <!-- Anket Seçenekleri Dinamik Yüklenir -->
            </div>
            <div id="pollInfoMessage" class="text-xs text-slate-400 font-medium text-center">
                <i class="fa-solid fa-lock text-pink-400 mr-1"></i> Bu anket yalnızca yönetici (Admin) tarafından yönetilebilir ve oylanabilir.
            </div>
        </section>

        <!-- Yorumlar Bölümü -->
        <section class="glass-card rounded-3xl p-6 md:p-8 space-y-6 shadow-xl">
            <div class="flex items-center justify-between border-b border-purple-500/20 pb-4">
                <div>
                    <h3 class="text-xl font-black text-white flex items-center gap-2"><i class="fa-regular fa-comments text-purple-400"></i> Değerlendirme ve Yorumlar</h3>
                    <p class="text-xs text-slate-400 mt-1">Çalışma hakkındaki akademik görüşlerinizi ve değerlendirmelerinizi paylaşabilirsiniz.</p>
                </div>
            </div>

            <!-- Yorum Ekleme Formu -->
            <form onsubmit="addComment(event)" class="space-y-3 bg-slate-900/50 p-5 rounded-2xl border border-purple-500/20">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
                    <input type="text" id="commentName" required placeholder="Adınız Soyadınız / Unvanınız" class="w-full bg-slate-900/90 border border-purple-500/30 rounded-xl px-4 py-2.5 text-xs text-slate-200 focus:outline-none focus:border-purple-500">
                    <input type="text" id="commentText" required placeholder="Yorumunuz veya değerlendirmeniz..." class="w-full bg-slate-900/90 border border-purple-500/30 rounded-xl px-4 py-2.5 text-xs text-slate-200 focus:outline-none focus:border-purple-500">
                </div>
                <div class="flex justify-end">
                    <button type="submit" class="px-5 py-2 bg-gradient-to-r from-purple-600 to-cyan-600 hover:from-purple-500 hover:to-cyan-500 text-white font-bold text-xs rounded-xl shadow-lg transition-all cursor-pointer">
                        <i class="fa-solid fa-paper-plane mr-1"></i> Yorumu Yayınla
                    </button>
                </div>
            </form>

            <!-- Yorum Listesi -->
            <div id="commentList" class="space-y-3"></div>
        </section>
    </main>

    <!-- Admin Yeni Anket Modalı -->
    <div id="newPollModal" class="fixed inset-0 z-50 flex items-center justify-center bg-black/80 backdrop-blur-sm hidden">
        <div class="glass-card w-full max-w-md p-6 rounded-3xl border border-pink-500/40 shadow-2xl space-y-4">
            <div class="flex justify-between items-center">
                <h3 class="text-sm font-bold text-white flex items-center gap-2"><i class="fa-solid fa-square-poll-vertical text-pink-400"></i> Yeni Anket Oluştur (Admin)</h3>
                <button onclick="closeNewPollModal()" class="text-slate-400 hover:text-white text-xs"><i class="fa-solid fa-xmark text-base"></i></button>
            </div>
            <div class="space-y-3">
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1">Anket Sorusu</label>
                    <input type="text" id="newPollQuestionInput" placeholder="Örn: Hangi tarihsel dönem daha ilgi çekici?" class="w-full bg-slate-900/90 border border-purple-500/40 rounded-xl px-4 py-2.5 text-xs text-slate-200 focus:outline-none focus:border-purple-500">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1">Seçenek 1</label>
                    <input type="text" id="pollOpt1" placeholder="Seçenek 1" class="w-full bg-slate-900/90 border border-purple-500/40 rounded-xl px-4 py-2 text-xs text-slate-200 focus:outline-none focus:border-purple-500 mb-2">
                    <label class="block text-xs font-semibold text-slate-300 mb-1">Seçenek 2</label>
                    <input type="text" id="pollOpt2" placeholder="Seçenek 2" class="w-full bg-slate-900/90 border border-purple-500/40 rounded-xl px-4 py-2 text-xs text-slate-200 focus:outline-none focus:border-purple-500">
                </div>
                <div class="flex gap-2 pt-2">
                    <button onclick="closeNewPollModal()" class="flex-1 py-2 bg-slate-800 hover:bg-slate-700 text-xs text-slate-300 font-bold rounded-xl transition-all">İptal</button>
                    <button onclick="saveNewPoll()" class="flex-1 py-2 bg-pink-600 hover:bg-pink-500 text-xs text-white font-bold rounded-xl transition-all">Anketi Yayınla</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Alt Bilgi / Footer -->
    <footer class="text-center py-8 text-xs text-slate-500 border-t border-purple-500/20 mt-16">
        <p>© 2026 Şaban Efe Ünsal — Tarih Performans Görevi. Tüm hakları saklıdır.</p>
    </footer>

    <!-- JavaScript Etkileşimler -->
    <script>
        let isAdmin = false;
        let comments = [
            { name: "Ahmet Yılmaz", text: "Harika bir performans görevi olmuş, tebrik ederim!", date: "26 Kasım 2026", reply: "" },
            { name: "Zeynep Demir", text: "Kaynakça ve nesnel ölçütler çok profesyonelce hazırlanmış.", date: "26 Kasım 2026", reply: "" }
        ];

        // Anket Verileri
        let currentPoll = {
            question: "Sizce dijital arşivler tarih araştırmalarını ne kadar kolaylaştırdı?",
            options: [
                { text: "Çok fazla kolaylaştırdı (Hızlı erişim)", votes: 14 },
                { text: "Kısmen kolaylaştırdı", votes: 5 },
                { text: "Geleneksel yöntemler daha iyi", votes: 2 }
            ],
            isVotingActive: true
        };

        // Admin butonu dinleyicisi
        document.addEventListener('DOMContentLoaded', () => {
            const adminBtn = document.getElementById('adminBtn');
            if (adminBtn) {
                adminBtn.addEventListener('click', (e) => {
                    e.preventDefault();
                    if (!isAdmin) {
                        document.getElementById('modalPasswordInput').value = '';
                        document.getElementById('modalError').classList.add('hidden');
                        document.getElementById('adminModal').classList.remove('hidden');
                    } else {
                        isAdmin = false;
                        document.getElementById('adminStatus').classList.add('hidden');
                        adminBtn.innerText = 'Admin Girişi';
                        document.getElementById('adminPanelSection').classList.add('hidden');
                        document.getElementById('adminPollControls').classList.add('hidden');
                        showToast("Yönetici oturumu kapatıldı.", "info");
                        renderComments();
                        renderPoll();
                    }
                });
            }
            renderComments();
            renderPoll();
        });

        function closeAdminModal() {
            document.getElementById('adminModal').classList.add('hidden');
        }

        function submitAdminPassword() {
            const pass = document.getElementById('modalPasswordInput').value;
            const errEl = document.getElementById('modalError');
            if (pass === "fenerbahçe1907" || pass === "fenerbahce1907") {
                isAdmin = true;
                closeAdminModal();
                document.getElementById('adminStatus').classList.remove('hidden');
                document.getElementById('adminBtn').innerText = 'Çıkış Yap';
                document.getElementById('adminPanelSection').classList.remove('hidden');
                document.getElementById('adminPollControls').classList.remove('hidden');
                showToast("Yönetici girişi başarılı!", "success");
                renderComments();
                renderPoll();
            } else {
                errEl.innerText = "Hatalı şifre! Tekrar deneyin.";
                errEl.classList.remove('hidden');
            }
        }

        function showToast(message, type = "success") {
            const toast = document.getElementById('customToast');
            const msgEl = document.getElementById('toastMessage');
            const iconEl = document.getElementById('toastIcon');
            
            msgEl.innerText = message;
            if(type === "success") {
                iconEl.className = "fa-solid fa-circle-check text-emerald-400 text-base";
            } else {
                iconEl.className = "fa-solid fa-circle-info text-cyan-400 text-base";
            }

            toast.classList.remove('translate-y-20', 'opacity-0');
            setTimeout(() => {
                toast.classList.add('translate-y-20', 'opacity-0');
            }, 3000);
        }

        function saveAdminChanges() {
            let newTitle = document.getElementById('adminTitleInput').value;
            let newContent = document.getElementById('adminContentInput').value;
            document.getElementById('displayTitle').innerText = "1. " + newTitle;
            document.getElementById('displayContent').innerText = newContent;
            showToast("Değişiklikler başarıyla kaydedildi!");
        }

        function checkAnswer(button, isCorrect, questionNum) {
            const feedbackEl = document.getElementById(`feedback-${questionNum}`);
            feedbackEl.classList.remove('hidden');
            if (isCorrect) {
                feedbackEl.className = "text-xs font-semibold text-emerald-400 mt-2";
                feedbackEl.innerHTML = "🎉 Doğru cevap! Tebrikler.";
                button.classList.add('border-emerald-500', 'bg-emerald-500/20');
            } else {
                feedbackEl.className = "text-xs font-semibold text-rose-400 mt-2";
                feedbackEl.innerHTML = "❌ Yanlış cevap, tekrar deneyebilirsin.";
                button.classList.add('border-rose-500', 'bg-rose-500/20');
            }
        }

        // Anket Fonksiyonları
        function renderPoll() {
            document.getElementById('pollQuestionTitle').innerText = currentPoll.question;
            const container = document.getElementById('pollOptionsContainer');
            const infoMsg = document.getElementById('pollInfoMessage');
            const statusBadge = document.getElementById('pollStatusBadge');
            const toggleBtn = document.getElementById('togglePollVotingBtn');
            
            container.innerHTML = '';

            if (currentPoll.isVotingActive) {
                statusBadge.className = "text-[10px] font-bold px-2 py-0.5 rounded-full bg-emerald-500/20 text-emerald-400 border border-emerald-500/30";
                statusBadge.innerText = "Oylama Açık";
                if (toggleBtn) {
                    toggleBtn.className = "px-3 py-1.5 bg-amber-600 hover:bg-amber-500 text-white font-bold text-xs rounded-xl transition-all cursor-pointer";
                    toggleBtn.innerHTML = '<i class="fa-solid fa-pause"></i> Oylamayı Durdur';
                }
            } else {
                statusBadge.className = "text-[10px] font-bold px-2 py-0.5 rounded-full bg-rose-500/20 text-rose-400 border border-rose-500/30";
                statusBadge.innerText = "Oylama Kapalı";
                if (toggleBtn) {
                    toggleBtn.className = "px-3 py-1.5 bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-xs rounded-xl transition-all cursor-pointer";
                    toggleBtn.innerHTML = '<i class="fa-solid fa-play"></i> Oylamayı Başlat';
                }
            }

            let totalVotes = currentPoll.options.reduce((sum, opt) => sum + opt.votes, 0);
            if (totalVotes === 0) totalVotes = 1;

            currentPoll.options.forEach((opt, idx) => {
                let percent = Math.round((opt.votes / totalVotes) * 100);
                let btn = document.createElement('div');
                btn.className = "space-y-1.5 bg-slate-900/40 p-3 rounded-2xl border border-purple-500/20";

                if (isAdmin) {
                    btn.innerHTML = `
                        <div class="flex justify-between items-center text-xs font-medium text-slate-300">
                            <span>${opt.text}</span>
                            <div class="flex items-center gap-3">
                                <span class="text-pink-400 font-bold">${opt.votes} Oy (%${percent})</span>
                                <button onclick="votePoll(${idx})" ${!currentPoll.isVotingActive ? 'disabled' : ''} class="px-2.5 py-1 ${currentPoll.isVotingActive ? 'bg-pink-600/80 hover:bg-pink-500 cursor-pointer' : 'bg-slate-700 opacity-50 cursor-not-allowed'} text-white text-[11px] font-bold rounded-lg transition-all">+1 Oy Ekle</button>
                            </div>
                        </div>
                        <div class="w-full bg-slate-900/90 rounded-full h-2.5 overflow-hidden border border-purple-500/20">
                            <div class="bg-gradient-to-r from-purple-500 to-pink-500 h-full rounded-full transition-all duration-500" style="width: ${percent}%"></div>
                        </div>
                    `;
                } else {
                    btn.innerHTML = `
                        <div class="flex justify-between text-xs font-medium text-slate-300">
                            <span>${opt.text}</span>
                            <span class="text-pink-400 font-bold">${opt.votes} Oy (%${percent})</span>
                        </div>
                        <div class="w-full bg-slate-900/90 rounded-full h-2.5 overflow-hidden border border-purple-500/20">
                            <div class="bg-gradient-to-r from-purple-500 to-pink-500 h-full rounded-full transition-all duration-500" style="width: ${percent}%"></div>
                        </div>
                    `;
                }
                container.appendChild(btn);
            });

            if (isAdmin) {
                infoMsg.innerHTML = '<span class="text-emerald-400 font-semibold"><i class="fa-solid fa-unlock mr-1"></i> Yönetici modu aktif: Oylamayı başlatıp durdurabilir, oy ekleyebilir veya yeni anket açabilirsiniz.</span>';
            } else {
                infoMsg.innerHTML = '<i class="fa-solid fa-lock text-pink-400 mr-1"></i> Bu anket yalnızca yönetici (Admin) tarafından yönetilebilir ve oylanabilir.';
            }
        }

        function togglePollVoting() {
            if (!isAdmin) return;
            currentPoll.isVotingActive = !currentPoll.isVotingActive;
            renderPoll();
            showToast(currentPoll.isVotingActive ? "Oylama başlatıldı!" : "Oylama durduruldu!", "info");
        }

        function votePoll(index) {
            if (!isAdmin) {
                showToast("Ankette değişiklik yapma yetkiniz yok!", "info");
                return;
            }
            if (!currentPoll.isVotingActive) {
                showToast("Oylama şu an kapalı!", "info");
                return;
            }
            currentPoll.options[index].votes++;
            renderPoll();
            showToast("Admin oyu eklendi!");
        }

        function openNewPollModal() {
            if (!isAdmin) return;
            document.getElementById('newPollQuestionInput').value = '';
            document.getElementById('pollOpt1').value = '';
            document.getElementById('pollOpt2').value = '';
            document.getElementById('newPollModal').classList.remove('hidden');
        }

        function closeNewPollModal() {
            document.getElementById('newPollModal').classList.add('hidden');
        }

        function saveNewPoll() {
            const q = document.getElementById('newPollQuestionInput').value.trim();
            const o1 = document.getElementById('pollOpt1').value.trim();
            const o2 = document.getElementById('pollOpt2').value.trim();

            if (!q || !o1 || !o2) {
                showToast("Lütfen tüm alanları doldurun!", "info");
                return;
            }

            currentPoll = {
                question: q,
                options: [
                    { text: o1, votes: 0 },
                    { text: o2, votes: 0 }
                ],
                hasVoted: false
            };

            closeNewPollModal();
            renderPoll();
            showToast("Yeni anket başarıyla yayınlandı!");
        }

        function resetPollVotes() {
            if (!isAdmin) return;
            currentPoll.options.forEach(o => o.votes = 0);
            currentPoll.hasVoted = false;
            renderPoll();
            showToast("Anket oyları sıfırlandı.");
        }

        function addComment(event) {
            event.preventDefault();
            const name = document.getElementById('commentName').value;
            const text = document.getElementById('commentText').value;
            comments.unshift({ name, text, date: "Bugün", reply: "" });
            document.getElementById('commentName').value = '';
            document.getElementById('commentText').value = '';
            renderComments();
            showToast("Yorumunuz başarıyla eklendi!");
        }

        function deleteComment(index) {
            if (isAdmin) {
                comments.splice(index, 1);
                renderComments();
                showToast("Yorum silindi.");
            } else {
                showToast("Bu işlem için yetki gerekiyor!", "info");
            }
        }

        function replyComment(index) {
            if (!isAdmin) return;
            // Özel prompt modalı yerine hızlı inline input
            const existingInput = document.getElementById(`reply-box-${index}`);
            if (existingInput) {
                existingInput.remove();
                return;
            }
            const commentDiv = document.getElementById(`comment-item-${index}`);
            const replyBox = document.createElement('div');
            replyBox.id = `reply-box-${index}`;
            replyBox.className = "mt-3 flex gap-2";
            replyBox.innerHTML = `
                <input type="text" id="reply-input-${index}" placeholder="Yönetici yanıtını yazın..." class="flex-1 bg-slate-950 border border-cyan-500/40 rounded-xl px-3 py-1.5 text-xs text-slate-200 focus:outline-none">
                <button onclick="submitReply(${index})" class="px-3 py-1.5 bg-cyan-600 hover:bg-cyan-500 text-white font-bold text-xs rounded-xl cursor-pointer">Gönder</button>
            `;
            commentDiv.appendChild(replyBox);
        }

        function submitReply(index) {
            const input = document.getElementById(`reply-input-${index}`);
            if (input && input.value.trim() !== "") {
                comments[index].reply = input.value.trim();
                renderComments();
                showToast("Yönetici yanıtı eklendi!");
            }
        }

        function renderComments() {
            const listEl = document.getElementById('commentList');
            if (!listEl) return;
            listEl.innerHTML = '';
            comments.forEach((c, idx) => {
                let div = document.createElement('div');
                div.id = `comment-item-${idx}`;
                div.className = "bg-slate-900/50 p-4 rounded-xl border border-purple-500/20 space-y-2";
                
                let replyHtml = c.reply ? `
                    <div class="mt-3 ml-4 p-3 bg-purple-950/40 border-l-2 border-purple-400 rounded-r-xl text-xs text-purple-200">
                        <span class="font-bold text-purple-300 block mb-0.5"><i class="fa-solid fa-shield text-[10px]"></i> Şaban Efe Ünsal (Yönetici Yanıtı):</span>
                        ${c.reply}
                    </div>
                ` : '';

                div.innerHTML = `
                    <div class="flex justify-between items-start">
                        <div class="space-y-1">
                            <div class="flex items-center gap-2">
                                <span class="font-bold text-xs text-purple-300">${c.name}</span>
                                <span class="text-[10px] text-slate-500">${c.date}</span>
                            </div>
                            <p class="text-xs text-slate-300">${c.text}</p>
                        </div>
                        ${isAdmin ? `
                            <div class="flex gap-2">
                                <button onclick="replyComment(${idx})" class="text-cyan-400 hover:text-cyan-300 text-xs font-bold px-2 py-1 bg-cyan-500/10 rounded-lg border border-cyan-500/20 cursor-pointer">Yanıtla</button>
                                <button onclick="deleteComment(${idx})" class="text-rose-400 hover:text-rose-300 text-xs font-bold px-2 py-1 bg-rose-500/10 rounded-lg border border-rose-500/20 cursor-pointer">Sil</button>
                            </div>
                        ` : ''}
                    </div>
                    ${replyHtml}
                `;
                listEl.appendChild(div);
            });
        }
    </script>
</body>
</html>
```
