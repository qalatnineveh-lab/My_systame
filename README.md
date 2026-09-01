<!DOCTYPE html>
<html lang="ckb" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>داشبۆردی پيرچاوش</title>
<script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gradient-to-br from-slate-900 via-zinc-900 to-stone-900 text-gray-100 font-sans min-h-screen">

<!-- ١. فۆرمی چوونەژوورەوە -->
<div id="loginSection" class="flex items-center justify-center h-screen px-4">
<div class="bg-zinc-800/80 backdrop-blur-xl border border-zinc-700/60 p-8 rounded-2xl shadow-2xl w-full max-w-md relative overflow-hidden">
<div class="absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-emerald-500 via-teal-500 to-cyan-500"></div>

<div class="text-center mb-8">
<div class="inline-flex items-center justify-center w-16 h-16 rounded-2xl bg-teal-500/10 text-teal-400 mb-4 border border-teal-500/20 shadow-inner">
<svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z"></path>
</svg>
</div>
<h2 class="text-2xl font-black tracking-wide text-white">سیستەمی بەڕێوەبردن</h2>
<p class="text-xs text-zinc-400 mt-1">تکایە بۆ چوونەژوورەوە زانیارییەکانت بنووسە</p>
</div>

<div class="space-y-5">
<div>
<label class="block text-zinc-300 text-xs font-bold mb-2">ناوی بەکارهێنەر</label>
<input type="text" id="loginUser" class="w-full px-4 py-3 bg-zinc-900/90 border border-zinc-700 rounded-xl text-white placeholder-zinc-500 focus:outline-none focus:ring-2 focus:ring-teal-500 focus:border-transparent transition text-sm" placeholder="admin">
</div>
<div>
<label class="block text-zinc-300 text-xs font-bold mb-2">تێپەڕەوشە</label>
<input type="password" id="loginPass" class="w-full px-4 py-3 bg-zinc-900/90 border border-zinc-700 rounded-xl text-white placeholder-zinc-500 focus:outline-none focus:ring-2 focus:ring-teal-500 focus:border-transparent transition text-sm" placeholder="••••••••">
</div>
<button onclick="login()" class="w-full bg-gradient-to-r from-teal-500 to-emerald-600 hover:from-teal-600 hover:to-emerald-700 text-white font-bold py-3 px-4 rounded-xl shadow-lg shadow-teal-900/30 transition transform active:scale-[0.98] text-sm">چوونەژوورەوە</button>
</div>
</div>
</div>

<!-- ٢. داشبۆردی سەرەکی -->
<div id="dashboardSection" class="hidden min-h-screen flex flex-col">
<header class="bg-zinc-900/90 backdrop-blur-md border-b border-zinc-800 text-white shadow-xl px-8 py-4 flex justify-between items-center sticky top-0 z-50">
<div>
<h1 class="text-2xl font-black tracking-wider bg-gradient-to-r from-teal-400 to-emerald-400 bg-clip-text text-transparent">پيرچاوش</h1>
<p class="text-xs text-zinc-400 mt-0.5">سیستەمی بەڕێوەبردنی مواد، پشکنین، غەیبات، مۆڵەت، کڕین، فرۆشتن، مووچە و مسرەف</p>
</div>
<div class="flex items-center gap-4">
<span id="welcomeUser" class="text-xs font-bold bg-zinc-800 border border-zinc-700 px-3 py-1.5 rounded-lg text-teal-300 shadow-sm"></span>
<button onclick="logout()" class="bg-rose-500/10 hover:bg-rose-500/20 text-rose-400 border border-rose-500/30 px-4 py-2 rounded-xl transition text-xs font-bold shadow-sm">چوونە دەرەوە</button>
</div>
</header>

<div class="flex-1 p-6 max-w-[98%] mx-auto w-full">
<!-- تبەکان -->
<div id="tabsNavContainer" class="flex flex-wrap gap-2 mb-6 border-b border-zinc-800 pb-4">
<button onclick="switchTab('tab1')" id="btn-tab1" class="tab-btn bg-teal-600 text-white px-4 py-2 rounded-xl font-bold shadow-md text-xs transition">١. تەیبڵی مواد و پشکنین</button>
<button onclick="switchTab('tab2')" id="btn-tab2" class="tab-btn bg-zinc-800 text-zinc-300 px-4 py-2 rounded-xl font-bold shadow-sm text-xs hover:bg-zinc-700 transition">٢. سیستەمی غەیبات و مۆڵەت</button>
<button onclick="switchTab('tab3')" id="btn-tab3" class="tab-btn bg-zinc-800 text-zinc-300 px-4 py-2 rounded-xl font-bold shadow-sm text-xs hover:bg-zinc-700 transition">٣. بەڕێوەبردنی یوزەرەکان</button>
<button onclick="switchTab('tab4')" id="btn-tab4" class="tab-btn bg-zinc-800 text-zinc-300 px-4 py-2 rounded-xl font-bold shadow-sm text-xs hover:bg-zinc-700 transition">٤. هەموو شتێک (ڕاپۆرت)</button>
<button onclick="switchTab('tab5')" id="btn-tab5" class="tab-btn bg-zinc-800 text-zinc-300 px-4 py-2 rounded-xl font-bold shadow-sm text-xs hover:bg-zinc-700 transition">٥. کڕین، فرۆشتن و قەرز</button>
<button onclick="switchTab('tab6')" id="btn-tab6" class="tab-btn bg-zinc-800 text-zinc-300 px-4 py-2 rounded-xl font-bold shadow-sm text-xs hover:bg-zinc-700 transition">٦. مووچە و مسرەف</button>
</div>

<!-- بەشی یەکەم: مواد و فحصەکان -->
<div id="content-tab1" class="tab-content bg-zinc-900 border border-zinc-800 p-6 rounded-2xl shadow-xl">
<h3 class="text-base font-bold text-zinc-200 mb-4">زیادکردنی زانیاری مواد و پشکنین</h3>
<input type="hidden" id="editIndex1" value="-1">

<div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-4">
<div>
<label class="block text-zinc-400 text-xs mb-1">جوری مواد</label>
<select id="mJoryMawad" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-sm focus:outline-none focus:ring-2 focus:ring-teal-500" onchange="renderFahsInputs()">
<option value="کاز">کاز</option>
<option value="رون">رۆن</option>
<option value="رون رەش">رۆن ڕەش</option>
<option value="رون زەرد">رۆن زەرد</option>
<option value="قیر">قیر</option>
<option value="فلۆین">فلۆین</option>
<option value="Hfo">Hfo</option>
<option value="Vr">Vr</option>
<option value="رەشە">رەشە</option>
<option value="رۆن سیستەم">رۆن سیستەم</option>
<option value="کاز سیستەم">کاز سیستەم</option>
<option value="نفتای سیستەم">نفتای سیستەم</option>
<option value="مواد بۆیلەر">مواد بۆیلەر</option>
</select>
</div>

<div>
<label class="block text-zinc-400 text-xs mb-1">ناوی مواد</label>
<input type="text" id="mMawad" placeholder="ناوی مواد بنووسە" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-sm focus:outline-none focus:ring-2 focus:ring-teal-500">
</div>

<div>
<label class="block text-zinc-400 text-xs mb-1">کۆمێنت</label>
<input type="text" id="mComment" placeholder="تێبینی..." class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-sm focus:outline-none focus:ring-2 focus:ring-teal-500">
</div>
</div>

<div id="materialNotes" class="bg-amber-500/10 border-l-4 border-amber-500 p-3 mb-4 text-xs font-bold text-amber-400 rounded-xl"></div>

<div class="bg-zinc-950/50 p-4 rounded-xl border border-zinc-800 mb-4">
<label class="block text-zinc-300 text-xs font-bold mb-3">خانەکانی پشکنین (ئەنجامەکان بنوسە):</label>
<div id="fahsInputsContainer" class="grid grid-cols-2 md:grid-cols-4 gap-4"></div>
</div>

<div class="mb-6">
<button onclick="saveData1()" class="bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-2.5 px-6 rounded-xl transition text-xs shadow-lg shadow-emerald-900/30">پاشەکەوتکردنی تۆمار</button>
</div>

<div class="overflow-x-auto mt-6 rounded-xl border border-zinc-800">
<table class="w-full border-collapse text-right text-xs">
<thead>
<tr class="bg-zinc-800 text-zinc-300">
<th class="border-b border-zinc-700 px-3 py-3">Id</th>
<th class="border-b border-zinc-700 px-3 py-3">جوری مواد</th>
<th class="border-b border-zinc-700 px-3 py-3">مواد</th>
<th class="border-b border-zinc-700 px-3 py-3">ئەنجامی پشکنینەکان</th>
<th class="border-b border-zinc-700 px-3 py-3">کۆمێنت</th>
<th class="border-b border-zinc-700 px-3 py-3">کات و مێژوو</th>
<th class="border-b border-zinc-700 px-3 py-3">Delete</th>
<th class="border-b border-zinc-700 px-3 py-3">Edit</th>
</tr>
</thead>
<tbody id="tableBody1" class="divide-y divide-zinc-800 text-zinc-300"></tbody>
</table>
</div>
</div>

<!-- بەشی دووەم: سیستەمی غەیبات و مۆڵەت (جیابۆوە) -->
<div id="content-tab2" class="tab-content hidden bg-zinc-900 border border-zinc-800 p-6 rounded-2xl shadow-xl">
<div class="flex flex-wrap justify-between items-center mb-6 gap-4 bg-zinc-950/50 p-4 rounded-xl border border-zinc-800">
<div class="flex flex-wrap gap-4 items-end w-full md:w-auto">
<div>
<label class="block text-xs font-bold text-zinc-400 mb-1">ناوی عامل بۆ زیادکردن</label>
<input type="text" id="wNameInput" placeholder="ناوی عامل بنووسە" class="px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white w-60 text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
</div>
<div>
<label class="block text-xs font-bold text-zinc-400 mb-1">پیشاندانی مانگی:</label>
<select id="filterMonthSelect" onchange="renderTable2(); renderTable6();" class="px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 font-bold text-teal-400 min-w-[140px] text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
</select>
</div>
<div>
<button onclick="addNewWorker()" class="bg-teal-600 hover:bg-teal-700 text-white font-bold py-2.5 px-5 rounded-xl text-xs transition shadow-lg shadow-teal-900/30">زیادکردنی عامل</button>
</div>
</div>
<div class="flex flex-wrap gap-2">
<button onclick="exportMonthExcel()" class="bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-2.5 px-4 rounded-xl text-xs transition shadow">📥 داگرتنی مانگی ئێستا (Excel)</button>
<button onclick="startNewMonth()" class="bg-purple-600 hover:bg-purple-700 text-white font-bold py-2.5 px-4 rounded-xl text-xs transition shadow">🔄 دەستپێکردنی مانگی نوێ</button>
</div>
</div>

<div class="flex items-center gap-4 mb-4 text-xs font-bold bg-zinc-950/40 p-3 rounded-xl border border-zinc-800">
<span class="flex items-center gap-1.5"><span class="w-3 h-3 rounded-full bg-emerald-500 inline-block"></span> حازر (Present)</span>
<span class="flex items-center gap-1.5"><span class="w-3 h-3 rounded-full bg-rose-500 inline-block"></span> غەیاب (Absent)</span>
<span class="flex items-center gap-1.5"><span class="w-3 h-3 rounded-full bg-amber-500 inline-block"></span> مۆڵەت (Leave)</span>
<span class="text-zinc-500 text-[11px] mr-auto">(کرتە لەسەر هەر خانه بکە بۆ گۆڕینی دۆخەکە)</span>
</div>

<div class="overflow-x-auto rounded-xl border border-zinc-800">
<table class="w-full border-collapse text-right text-xs">
<thead>
<tr id="daysHeaderRow" class="bg-zinc-800 text-zinc-300 text-center">
<th class="border-b border-zinc-700 px-2 py-3">Id</th>
<th class="border-b border-zinc-700 px-3 py-3 min-w-[120px] text-right">ناوی عامل</th>
<th class="border-b border-zinc-700 px-2 py-3">مانگ</th>
<th class="border-b border-zinc-700 px-2 py-3 bg-rose-500/10 text-rose-400 font-extrabold min-w-[70px]">غەیاب</th>
<th class="border-b border-zinc-700 px-2 py-3 bg-amber-500/10 text-amber-400 font-extrabold min-w-[70px]">مۆڵەت</th>
<th class="border-b border-zinc-700 px-2 py-3">Delete</th>
</tr>
</thead>
<tbody id="tableBody2" class="divide-y divide-zinc-800 text-zinc-300"></tbody>
</table>
</div>
</div>

<!-- بەشی سێیەم: زیادکردنی یوزەرەکان -->
<div id="content-tab3" class="tab-content hidden bg-zinc-900 border border-zinc-800 p-6 rounded-2xl shadow-xl max-w-2xl mx-auto">
<h3 class="text-base font-bold text-zinc-200 mb-4">زیادکردن و بەڕێوەبردنی یوزەرەکان</h3>

<div class="bg-zinc-950/50 p-4 rounded-xl border border-zinc-800 mb-6 space-y-4">
<h4 class="font-bold text-teal-400 text-xs">زیادکردنی یوزەری نوێ</h4>
<div class="grid grid-cols-1 md:grid-cols-3 gap-4">
<input type="text" id="newRegUser" placeholder="ناوی بەکارهێنەر" class="px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
<input type="password" id="newRegPass" placeholder="تێپەڕەوشە (پاسوۆرد)" class="px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
<select id="newRegRole" class="px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
<option value="admin">ادمین (هەموو شتێک)</option>
<option value="lab">مۆبایلی مختبر (تەنها فحص)</option>
</select>
</div>
<button onclick="addNewUser()" class="bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-2.5 px-4 rounded-xl w-full text-xs transition">تۆمارکردنی یوزەری نوێ</button>
</div>

<h4 class="font-bold text-zinc-300 mb-2 text-xs">لیستی یوزەرە تۆمارکراوەکان:</h4>
<div class="overflow-x-auto rounded-xl border border-zinc-800">
<table class="w-full border-collapse text-right text-xs">
<thead>
<tr class="bg-zinc-800 text-zinc-300">
<th class="border-b border-zinc-700 px-3 py-3">ناوی بەکارهێنەر</th>
<th class="border-b border-zinc-700 px-3 py-3">تێپەڕەوشە</th>
<th class="border-b border-zinc-700 px-3 py-3">ڕۆڵ (دەسەڵات)</th>
<th class="border-b border-zinc-700 px-3 py-3">سڕینەوە</th>
</tr>
</thead>
<tbody id="usersTableBody" class="divide-y divide-zinc-800 text-zinc-300"></tbody>
</table>
</div>
</div>

<!-- بەشی چوارەم: ڕاپۆرت -->
<div id="content-tab4" class="tab-content hidden bg-zinc-900 border border-zinc-800 p-6 rounded-2xl shadow-xl">
<h3 class="text-base font-bold text-zinc-200 mb-4">پوختەی گشتی و هەژماری قازانج و زیان (فایدە و خسار)</h3>

<div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-6">
<div class="bg-teal-500/10 p-5 rounded-2xl border border-teal-500/20">
<h4 class="text-zinc-400 text-xs font-bold">کۆی فرۆشتنی حازر (داهات)</h4>
<p id="reportTotalSales" class="text-2xl font-black text-teal-400 mt-2">٠</p>
</div>
<div class="bg-rose-500/10 p-5 rounded-2xl border border-rose-500/20">
<h4 class="text-zinc-400 text-xs font-bold">کۆی مسرەف و خەرجییەکان</h4>
<p id="reportTotalExpenses" class="text-2xl font-black text-rose-400 mt-2">٠</p>
</div>
<div id="profitCardBg" class="bg-emerald-500/10 p-5 rounded-2xl border border-emerald-500/20">
<h4 id="profitTitle" class="text-zinc-400 text-xs font-bold">پوختە (قازانج / فایدە)</h4>
<p id="reportNetProfit" class="text-2xl font-black text-emerald-400 mt-2">٠</p>
</div>
</div>

<div class="grid grid-cols-1 md:grid-cols-4 gap-4 mb-6">
<div class="bg-zinc-950/50 p-4 rounded-xl border border-zinc-800">
<h4 class="text-xs font-bold text-zinc-300 mb-1">ژمارەی عاملەکان</h4>
<p id="reportWorkersCount" class="text-lg font-bold text-teal-400">٠ عامل</p>
</div>
<div class="bg-zinc-950/50 p-4 rounded-xl border border-zinc-800">
<h4 class="text-xs font-bold text-zinc-300 mb-1">ژمارەی فحصەکان</h4>
<p id="reportFahsCount" class="text-lg font-bold text-cyan-400">٠ فحص</p>
</div>
<div class="bg-zinc-950/50 p-4 rounded-xl border border-zinc-800">
<h4 class="text-xs font-bold text-zinc-300 mb-1">ژمارەی مواد</h4>
<p id="reportMaterialsCount" class="text-lg font-bold text-amber-400">٠ مواد</p>
</div>
<div class="bg-zinc-950/50 p-4 rounded-xl border border-zinc-800">
<h4 class="text-xs font-bold text-zinc-300 mb-1">ژمارەی فرۆشتن و کڕین</h4>
<p id="reportTransCount" class="text-lg font-bold text-emerald-400">٠ مامەڵە</p>
</div>
</div>

<div class="grid grid-cols-1 md:grid-cols-2 gap-6">
<div class="bg-zinc-950/50 p-5 rounded-xl border border-zinc-800">
<h4 class="text-xs font-bold text-zinc-300 mb-2">کۆی گشتی قەرزەکان</h4>
<p id="reportTotalDebt" class="text-lg font-bold text-indigo-400">٠</p>
</div>
<div class="bg-zinc-950/50 p-5 rounded-xl border border-zinc-800">
<h4 class="text-xs font-bold text-zinc-300 mb-2">پارەی خەڵک لە لای ئێمە / پارەی ئێمە لە لای خەڵک</h4>
<p id="reportPeopleBalance" class="text-lg font-bold text-teal-400">٠</p>
</div>
</div>
</div>

<!-- بەشی پێنجەم: کڕین، فرۆشتن و قەرز -->
<div id="content-tab5" class="tab-content hidden bg-zinc-900 border border-zinc-800 p-6 rounded-2xl shadow-xl">
<h3 class="text-base font-bold text-zinc-200 mb-4">بەڕێوەبردنی کڕین، فرۆشتن، پارەی حازر و قەرز (دۆلار و دینار)</h3>

<div class="grid grid-cols-1 md:grid-cols-4 gap-4 mb-4 bg-zinc-950/50 p-4 rounded-xl border border-zinc-800">
<div>
<label class="block text-zinc-400 text-xs mb-1">ناوی کڕیار یان فرۆشیار</label>
<input type="text" id="tCustomerName" placeholder="ناوی کەسەکە..." class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
</div>
<div>
<label class="block text-zinc-400 text-xs mb-1">جۆری مواد / بابەت</label>
<select id="tItemType" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500" onchange="autoSelectUnit()">
<option value="قیر">قیر</option>
<option value="Hfo">Hfo</option>
<option value="Vr">Vr</option>
<option value="رۆن ڕەش">رۆن ڕەش</option>
<option value="کاز">کاز</option>
<option value="رۆن">رۆن</option>
<option value="گازوایل">گازوایل</option>
<option value="فلۆین">فلۆین</option>
<option value="ئاسن / شتومەک">ئاسن / شتومەک</option>
</select>
</div>
<div>
<label class="block text-zinc-400 text-xs mb-1">جۆری جووڵە</label>
<select id="tType" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
<option value="فرۆشتن">فرۆشتن (دەرچوون)</option>
<option value="کڕین">کڕین (هاتن)</option>
</select>
</div>
<div>
<label class="block text-zinc-400 text-xs mb-1">جۆری پارەدان</label>
<select id="tPaymentType" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
<option value="حازر">پارەی حازر (نقد)</option>
<option value="قەرز">قەرز</option>
</select>
</div>
<div>
<label class="block text-zinc-400 text-xs mb-1">بڕ / قەبارە</label>
<input type="number" id="tQuantity" placeholder="٠" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
</div>
<div>
<label class="block text-zinc-400 text-xs mb-1">یەکەی پێوانە</label>
<select id="tUnit" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
<option value="تەن">تەن (Ton)</option>
<option value="لتر">لتر (Liter)</option>
<option value="دانە">دانە (Piece)</option>
<option value="کۆڵ">کۆڵ (Barrel)</option>
</select>
</div>
<div>
<label class="block text-zinc-400 text-xs mb-1">جۆری دراو</label>
<select id="tCurrency" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
<option value="USD">دۆلار ($)</option>
<option value="IQD">دینار (IQD)</option>
</select>
</div>
<div>
<label class="block text-zinc-400 text-xs mb-1">نرخی یەکە</label>
<input type="number" id="tUnitPrice" placeholder="٠" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500">
</div>
<div class="md:col-span-4 flex justify-end">
<button onclick="saveTransaction()" class="bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-2.5 px-6 rounded-xl transition text-xs shadow-lg shadow-emerald-900/30">تۆمارکردنی مامەڵە</button>
</div>
</div>

<div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
<div class="bg-indigo-500/10 border border-indigo-500/20 p-4 rounded-xl flex justify-between items-center">
<div>
<h4 class="text-zinc-400 text-xs font-bold">کۆی قەرز بە دینار</h4>
<p id="totalDebtIQD" class="text-xl font-black text-indigo-400 mt-1">٠ دینار</p>
</div>
<span class="text-2xl">📊</span>
</div>
<div class="bg-teal-500/10 border border-teal-500/20 p-4 rounded-xl flex justify-between items-center">
<div>
<h4 class="text-zinc-400 text-xs font-bold">کۆی قەرز بە دۆلار</h4>
<p id="totalDebtUSD" class="text-xl font-black text-teal-400 mt-1">٠ $</p>
</div>
<span class="text-2xl">💵</span>
</div>
<div class="bg-amber-500/10 border border-amber-500/20 p-4 rounded-xl flex justify-between items-center">
<div>
<h4 class="text-zinc-400 text-xs font-bold">کۆی مامەڵەی حازر</h4>
<p id="totalCashSum" class="text-xl font-black text-amber-400 mt-1">٠</p>
</div>
<span class="text-2xl">💰</span>
</div>
</div>

<div class="overflow-x-auto rounded-xl border border-zinc-800">
<table class="w-full border-collapse text-right text-xs">
<thead>
<tr class="bg-zinc-800 text-zinc-300">
<th class="border-b border-zinc-700 px-3 py-3">Id</th>
<th class="border-b border-zinc-700 px-3 py-3">ناوی کەس / کڕیار</th>
<th class="border-b border-zinc-700 px-3 py-3">جۆری مواد</th>
<th class="border-b border-zinc-700 px-3 py-3">جۆر</th>
<th class="border-b border-zinc-700 px-3 py-3">بڕ و یەکە</th>
<th class="border-b border-zinc-700 px-3 py-3">نرخی یەکە</th>
<th class="border-b border-zinc-700 px-3 py-3">کۆی گشتی</th>
<th class="border-b border-zinc-700 px-3 py-3">پارەدان</th>
<th class="border-b border-zinc-700 px-3 py-3">مێژوو</th>
<th class="border-b border-zinc-700 px-3 py-3">سڕینەوە</th>
</tr>
</thead>
<tbody id="tableBody5" class="divide-y divide-zinc-800 text-zinc-300"></tbody>
</table>
</div>
</div>

<!-- بەشی شەشەم: مووچەی عامل و مسرەفی معمل -->
<div id="content-tab6" class="tab-content hidden bg-zinc-900 border border-zinc-800 p-6 rounded-2xl shadow-xl">
<h3 class="text-base font-bold text-zinc-200 mb-4">حساباتی مووچەی عاملەکان و مسرەف / خەرجی معمل</h3>

<div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8">
<div class="bg-zinc-950/50 p-5 rounded-2xl border border-zinc-800">
<h4 class="font-bold text-teal-400 text-xs mb-3">١. ڕێکخستنی مووچەی عامل بۆ مانگ</h4>
<div class="space-y-3">
<div>
<label class="block text-zinc-400 text-xs mb-1">هەڵبژاردنی عامل</label>
<select id="workerSalarySelect" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs focus:outline-none focus:ring-2 focus:ring-teal-500"></select>
</div>
<div class="grid grid-cols-2 gap-2">
<div>
<label class="block text-zinc-400 text-xs mb-1">مووچەی بنەڕەتی مانگانە</label>
<input type="number" id="workerBaseSalary" placeholder="٠" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs">
</div>
<div>
<label class="block text-zinc-400 text-xs mb-1">جۆری دراوی مووچە</label>
<select id="workerSalaryCurrency" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs">
<option value="IQD">دینار (IQD)</option>
<option value="USD">دۆلار ($)</option>
</select>
</div>
</div>
<button onclick="saveWorkerSalarySetting()" class="w-full bg-teal-600 hover:bg-teal-700 text-white font-bold py-2.5 rounded-xl text-xs transition">پاشەکەوتکردنی مووچە</button>
</div>
</div>

<div class="bg-zinc-950/50 p-5 rounded-2xl border border-zinc-800">
<h4 class="font-bold text-amber-400 text-xs mb-3">٢. زیادکردنی مسرەف / خەرجی ڕۆژانەی معمل</h4>
<div class="space-y-3">
<div>
<label class="block text-zinc-400 text-xs mb-1">جۆری مسرەف / ناونیشان</label>
<input type="text" id="expenseTitle" placeholder="بۆ نموونە: چاککردنەوەی ئامێر، سووتەمەنی..." class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs">
</div>
<div class="grid grid-cols-2 gap-2">
<div>
<label class="block text-zinc-400 text-xs mb-1">بڕی پارە</label>
<input type="number" id="expenseAmount" placeholder="٠" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs">
</div>
<div>
<label class="block text-zinc-400 text-xs mb-1">جۆری دراو</label>
<select id="expenseCurrency" class="w-full px-3 py-2.5 border border-zinc-700 rounded-xl bg-zinc-800 text-white text-xs">
<option value="IQD">دینار (IQD)</option>
<option value="USD">دۆلار ($)</option>
</select>
</div>
</div>
<button onclick="saveExpense()" class="w-full bg-amber-600 hover:bg-amber-700 text-white font-bold py-2.5 rounded-xl text-xs transition">تۆمارکردنی مسرەف</button>
</div>
</div>
</div>

<h4 class="font-bold text-zinc-200 mb-2 text-xs">لیستی مووچەی عاملەکان (بە ڕەچاوکردنی غەیاب و مۆڵەت):</h4>
<div class="overflow-x-auto rounded-xl border border-zinc-800 mb-8">
<table class="w-full border-collapse text-right text-xs">
<thead>
<tr class="bg-zinc-800 text-zinc-300">
<th class="border-b border-zinc-700 px-3 py-3">ناوی عامل</th>
<th class="border-b border-zinc-700 px-3 py-3">مانگ</th>
<th class="border-b border-zinc-700 px-3 py-3 text-rose-400">کۆی غەیبات</th>
<th class="border-b border-zinc-700 px-3 py-3 text-amber-400">کۆی مۆڵەت</th>
<th class="border-b border-zinc-700 px-3 py-3">مووچەی بنەڕەتی</th>
<th class="border-b border-zinc-700 px-3 py-3 font-bold text-teal-400">مووچەی شایستە</th>
</tr>
</thead>
<tbody id="workerSalariesTableBody" class="divide-y divide-zinc-800 text-zinc-300"></tbody>
</table>
</div>

<h4 class="font-bold text-zinc-200 mb-2 text-xs">تۆماری مسرەف و خەرجییەکانی معمل:</h4>
<div class="overflow-x-auto rounded-xl border border-zinc-800">
<table class="w-full border-collapse text-right text-xs">
<thead>
<tr class="bg-zinc-800 text-zinc-300">
<th class="border-b border-zinc-700 px-3 py-3">Id</th>
<th class="border-b border-zinc-700 px-3 py-3">جۆری مسرەف / ناو</th>
<th class="border-b border-zinc-700 px-3 py-3">بڕی پارە</th>
<th class="border-b border-zinc-700 px-3 py-3">مێژوو</th>
<th class="border-b border-zinc-700 px-3 py-3">سڕینەوە</th>
</tr>
</thead>
<tbody id="expensesTableBody" class="divide-y divide-zinc-800 text-zinc-300"></tbody>
</table>
</div>
</div>

</div>
</div>

<script>
let currentUserRole = "admin";
let usersList = JSON.parse(localStorage.getItem('pirjaush_usersList')) || [
  { username: "admin", password: "123", role: "admin" }
];

let data1 = JSON.parse(localStorage.getItem('pirjaush_data1')) || [];
let data2 = JSON.parse(localStorage.getItem('pirjaush_data2')) || [];
let data5 = JSON.parse(localStorage.getItem('pirjaush_data5')) || [];
let workerSalaries = JSON.parse(localStorage.getItem('pirjaush_salaries')) || {}; 
let expensesList = JSON.parse(localStorage.getItem('pirjaush_expenses')) || [];

if(data2.length === 0) {
  let sampleNames = ["احمد", "محمود", "عمر"];
  sampleNames.forEach(name => {
    let daysObj = {};
    for(let i=1; i<=31; i++) daysObj[i] = 'present'; // دۆخی سەرەتایی حازر
    data2.push({ name: name, month: "مانگی ٨", days: daysObj });
  });
}

const fahsMap = {
  "قیر": ["فلاش", "فیسكو", "سولفير", "دةرزي"],
  "Hfo": ["فلاش", "فیسكو", "سولفير", "دةرزي"],
  "فلۆین": ["تواف", "فلاش", "فیسكو", "ئاو", "سولفير"],
  "رون رەش": ["تواف", "فلاش", "فیسكو", "ئاو", "سولفير"],
  "رۆن سیستەم": ["تواف", "فلاش", "فیسكو", "ئاو", "سولفير"],
  "نفتای سیستەم": ["تواف", "فلاش", "فیسكو", "ئاو", "سولفير"],
  "مواد بۆیلەر": ["تواف", "فلاش", "فیسكو", "ئاو", "سولفير"],
  "کاز": ["تواف", "فلاش", "سولفير", "کرمی"],
  "رون": ["تواف", "فلاش", "سولفير", "کرمی"]
};

function saveDataToStorage() {
  localStorage.setItem('pirjaush_usersList', JSON.stringify(usersList));
  localStorage.setItem('pirjaush_data1', JSON.stringify(data1));
  localStorage.setItem('pirjaush_data2', JSON.stringify(data2));
  localStorage.setItem('pirjaush_data5', JSON.stringify(data5));
  localStorage.setItem('pirjaush_salaries', JSON.stringify(workerSalaries));
  localStorage.setItem('pirjaush_expenses', JSON.stringify(expensesList));
}

function renderFahsInputs(existingValues = {}) {
  let material = document.getElementById('mJoryMawad').value;
  let container = document.getElementById('fahsInputsContainer');
  let notesContainer = document.getElementById('materialNotes');
  if(!container) return;
  container.innerHTML = '';
  notesContainer.innerHTML = '';
  notesContainer.style.display = "block";

  if (material === "قیر") {
    notesContainer.innerHTML = "📌 تێبینی: گەرمی دەبێت ١٣٥ بێت بۆ قیر | دەرزی قیر دەبێت ٢١ بێت.";
  } else if (material === "Hfo") {
    notesContainer.innerHTML = "📌 تێبینی: گەرمی دەبێت ٥٠ بێت بۆ Hfo | دەرزی دەبێت ٢٧ بێت.";
  } else {
    notesContainer.style.display = "none";
  }

  let fahsList = fahsMap[material] || ["تواف", "فلاش", "فیسكو", "سولفير"];
  fahsList.forEach(fahs => {
    let val = existingValues[fahs] || '';
    container.innerHTML += `<div> 
      <label class="block text-[11px] font-bold text-zinc-400 mb-1">${fahs}</label>
      <input type="text" data-fahs-name="${fahs}" value="${val}" placeholder="نتيجة..." class="fahs-input w-full px-3 py-2 border border-zinc-700 rounded-xl text-xs bg-zinc-800 text-white focus:outline-none focus:ring-2 focus:ring-teal-500">
    </div>`;
  });
}

function autoSelectUnit() {
  let itemType = document.getElementById('tItemType').value;
  let unitSelect = document.getElementById('tUnit');
  if(!unitSelect) return;

  if (["قیر", "Hfo", "Vr", "رۆن ڕەش"].includes(itemType)) {
    unitSelect.value = "تەن";
  } else if (["کاز", "رۆن", "گازوایل", "فلۆین"].includes(itemType)) {
    unitSelect.value = "لتر";
  } else {
    unitSelect.value = "دانە";
  }
}

window.onload = function() {
  renderFahsInputs();
  autoSelectUnit();
  updateMonthDropdown();
  renderUsersTable();
  renderTable1();
  renderTable2();
  renderTable5();
  renderTable6();
  updateReports();
}

function login() {
  let u = document.getElementById('loginUser').value.trim();
  let p = document.getElementById('loginPass').value.trim();
  let foundUser = usersList.find(user => user.username === u && user.password === p);

  if(foundUser) {
    currentUserRole = foundUser.role || "admin";
    document.getElementById('loginSection').classList.add('hidden');
    document.getElementById('dashboardSection').classList.remove('hidden');
    document.getElementById('welcomeUser').innerText = "بەخێر هاتیت، " + foundUser.username + " (" + (currentUserRole === 'admin' ? 'ادمین' : 'مۆبایلی مختبر') + ")";
    
    let tabsNav = document.getElementById('tabsNavContainer');
    if(currentUserRole === 'lab') {
      tabsNav.style.display = 'none';
      switchTab('tab1');
    } else {
      tabsNav.style.display = 'flex';
      updateMonthDropdown();
      renderTable1();
      renderTable2();
      renderTable5();
      renderTable6();
      renderUsersTable();
      updateReports();
    }
  } else {
    alert("ناوی بەکارهێنەر یان تێپەڕەوشە هەڵەیە!");
  }
}

function logout() {
  document.getElementById('dashboardSection').classList.add('hidden');
  document.getElementById('loginSection').classList.remove('hidden');
}

function switchTab(tabId) {
  if(currentUserRole === 'lab' && tabId !== 'tab1') {
    alert("تۆ تەنها دەسەڵاتی بینینی بەشی فحص (مۆبایلی مختبر)ت هەیە!");
    return;
  }
  document.querySelectorAll('.tab-content').forEach(c => c.classList.add('hidden'));
  document.querySelectorAll('.tab-btn').forEach(b => {
    b.classList.remove('bg-teal-600', 'text-white', 'shadow-md');
    b.classList.add('bg-zinc-800', 'text-zinc-300', 'shadow-sm');
  });

  let targetContent = document.getElementById('content-' + tabId);
  if(targetContent) targetContent.classList.remove('hidden');
  let btn = document.getElementById('btn-' + tabId);
  if(btn) {
    btn.classList.remove('bg-zinc-800', 'text-zinc-300', 'shadow-sm');
    btn.classList.add('bg-teal-600', 'text-white', 'shadow-md');
  }

  if(tabId === 'tab6') renderTable6();
  updateReports();
}

function saveData1() {
  let jMawad = document.getElementById('mJoryMawad').value;
  let mawad = document.getElementById('mMawad').value;
  let comment = document.getElementById('mComment').value;
  let editIdx = document.getElementById('editIndex1').value;

  if(!mawad) return alert("تکایە خانەی مواد پڕبکەرەوە!");

  let fahsResults = {};
  document.querySelectorAll('.fahs-input').forEach(input => {
    let name = input.getAttribute('data-fahs-name');
    let val = input.value.trim();
    if(val) fahsResults[name] = val;
  });

  let now = new Date();
  let dateTimeStr = now.toLocaleDateString() + ' ' + now.toLocaleTimeString();

  if(editIdx === "-1") {
    data1.push({ jMawad, mawad, fahsResults, comment, datetime: dateTimeStr });
  } else {
    data1[editIdx] = { jMawad, mawad, fahsResults, comment, datetime: data1[editIdx].datetime };
    document.getElementById('editIndex1').value = "-1";
  }

  saveDataToStorage();
  document.getElementById('mMawad').value = '';
  document.getElementById('mComment').value = '';
  renderFahsInputs();
  renderTable1();
  updateReports();
}

function renderTable1() {
  let tbody = document.getElementById('tableBody1');
  if(!tbody) return;
  tbody.innerHTML = '';
  data1.forEach((item, index) => {
    let fahsText = Object.entries(item.fahsResults).map(([k, v]) => `<span class="bg-teal-500/10 text-teal-300 border border-teal-500/20 px-2 py-0.5 rounded-lg text-[11px] ml-1">${k}: ${v}</span>`).join(' ');

    tbody.innerHTML += `<tr class="hover:bg-zinc-800/50 transition">
      <td class="border-b border-zinc-800 px-3 py-3">${index + 1}</td>
      <td class="border-b border-zinc-800 px-3 py-3">${item.jMawad}</td>
      <td class="border-b border-zinc-800 px-3 py-3 font-bold text-white">${item.mawad}</td>
      <td class="border-b border-zinc-800 px-3 py-3">${fahsText || 'هیچ نەنووسراوە'}</td>
      <td class="border-b border-zinc-800 px-3 py-3">${item.comment || '-'}</td>
      <td class="border-b border-zinc-800 px-3 py-3 text-zinc-400 text-[11px]">${item.datetime}</td>
      <td class="border-b border-zinc-800 px-3 py-3"><button onclick="deleteData1(${index})" class="text-rose-400 hover:text-rose-300 font-bold">🗑️</button></td>
      <td class="border-b border-zinc-800 px-3 py-3"><button onclick="editData1(${index})" class="text-teal-400 hover:text-teal-300 font-bold">✏️</button></td>
    </tr>`;
  });
}

function deleteData1(index) {
  if(confirm("دڵنیایت لە سڕینەوەی ئەم فحصە؟")) {
    data1.splice(index, 1);
    saveDataToStorage();
    renderTable1();
    updateReports();
  }
}

function editData1(index) {
  let item = data1[index];
  document.getElementById('mJoryMawad').value = item.jMawad;
  document.getElementById('mMawad').value = item.mawad;
  document.getElementById('mComment').value = item.comment;
  document.getElementById('editIndex1').value = index;
  renderFahsInputs(item.fahsResults);
}

// ================= بەشی غیاب و مۆڵەت (هەموارکراو) =================
function updateMonthDropdown() {
  let select = document.getElementById('filterMonthSelect');
  if(!select) return;
  let months = ["مانگی 1", "مانگی 2", "مانگی 3", "مانگی 4", "مانگی 5", "مانگی 6", "مانگی 7", "مانگی 8", "مانگی 9", "مانگی 10", "مانگی 11", "مانگی 12", "مانگی ٨"];
  let currentVal = select.value || "مانگی 8";
  select.innerHTML = '';
  months.forEach(m => {
    select.innerHTML += `<option value="${m}" ${m === currentVal ? 'selected' : ''}>${m}</option>`;
  });
}

function addNewWorker() {
  let nameInput = document.getElementById('wNameInput');
  let name = nameInput.value.trim();
  let month = document.getElementById('filterMonthSelect').value;
  if(!name) return alert("تکایە ناوی عامل بنووسە!");

  let daysObj = {};
  for(let i=1; i<=31; i++) daysObj[i] = 'present'; // پیشفرض حازر
  data2.push({ name: name, month: month, days: daysObj });
  nameInput.value = '';
  saveDataToStorage();
  renderTable2();
  renderTable6();
  updateReports();
}

function toggleDayStatus(workerIndex, dayNum) {
  let currentMonth = document.getElementById('filterMonthSelect').value;
  let filteredWorkers = data2.filter(w => w.month === currentMonth);
  let targetWorker = filteredWorkers[workerIndex];
  let realIndex = data2.indexOf(targetWorker);

  if(realIndex !== -1) {
    if(!data2[realIndex].days) data2[realIndex].days = {};
    let currentStatus = data2[realIndex].days[dayNum] || 'present';
    
    // سێ دۆخەکە: present -> absent -> leave -> present
    if(currentStatus === 'present') {
      data2[realIndex].days[dayNum] = 'absent'; // غەیاب
    } else if(currentStatus === 'absent') {
      data2[realIndex].days[dayNum] = 'leave'; // مۆڵەت
    } else {
      data2[realIndex].days[dayNum] = 'present'; // حازر
    }

    saveDataToStorage();
    renderTable2();
    renderTable6();
  }
}

function renderTable2() {
  let headerRow = document.getElementById('daysHeaderRow');
  let tbody = document.getElementById('tableBody2');
  let currentMonth = document.getElementById('filterMonthSelect').value;
  if(!headerRow || !tbody) return;

  let headersHTML = `<th class="border-b border-zinc-700 px-2 py-3">Id</th>
    <th class="border-b border-zinc-700 px-3 py-3 min-w-[120px] text-right">ناوی عامل</th>
    <th class="border-b border-zinc-700 px-2 py-3">مانگ</th>`;
  for(let i=1; i<=31; i++) {
    headersHTML += `<th class="border-b border-zinc-700 px-1 py-3 text-center text-[11px]">${i}</th>`;
  }
  headersHTML += `<th class="border-b border-zinc-700 px-2 py-3 bg-rose-500/10 text-rose-400 font-extrabold min-w-[70px]">غەیاب</th>
    <th class="border-b border-zinc-700 px-2 py-3 bg-amber-500/10 text-amber-400 font-extrabold min-w-[70px]">مۆڵەت</th>
    <th class="border-b border-zinc-700 px-2 py-3">Delete</th>`;
  headerRow.innerHTML = headersHTML;

  tbody.innerHTML = '';
  let filteredWorkers = data2.filter(w => w.month === currentMonth);

  filteredWorkers.forEach((worker, wIndex) => {
    let absentCount = 0;
    let leaveCount = 0;
    let daysHTML = '';

    for(let i=1; i<=31; i++) {
      if(!worker.days) worker.days = {};
      let status = worker.days[i] || 'present';
      let bgClass = "bg-emerald-500/20 text-emerald-400 hover:bg-emerald-500/30";
      let label = "ح";
      if(status === 'absent') {
        bgClass = "bg-rose-500/30 text-rose-300 hover:bg-rose-500/40";
        label = "غ";
        absentCount++;
      } else if(status === 'leave') {
        bgClass = "bg-amber-500/30 text-amber-300 hover:bg-amber-500/40";
        label = "م";
        leaveCount++;
      }
      daysHTML += `<td class="border-b border-zinc-800 p-1 text-center">
        <button onclick="toggleDayStatus(${wIndex}, ${i})" class="w-6 h-6 rounded-md font-bold text-[11px] transition ${bgClass}" title="کرتە بۆ گۆڕین">${label}</button>
      </td>`;
    }

    let realIdx = data2.indexOf(worker);
    tbody.innerHTML += `<tr class="hover:bg-zinc-800/50 transition">
      <td class="border-b border-zinc-800 px-2 py-3">${wIndex + 1}</td>
      <td class="border-b border-zinc-800 px-3 py-3 font-bold text-white">${worker.name}</td>
      <td class="border-b border-zinc-800 px-2 py-3 text-zinc-400 text-[11px]">${worker.month}</td>
      ${daysHTML}
      <td class="border-b border-zinc-800 px-2 py-3 bg-rose-500/5 font-extrabold text-rose-400 text-center">${absentCount}</td>
      <td class="border-b border-zinc-800 px-2 py-3 bg-amber-500/5 font-extrabold text-amber-400 text-center">${leaveCount}</td>
      <td class="border-b border-zinc-800 px-2 py-3 text-center"><button onclick="deleteWorker(${realIdx})" class="text-rose-400 hover:text-rose-300 font-bold">🗑️</button></td>
    </tr>`;
  });
}

function deleteWorker(index) {
  if(confirm("دڵنیایت لە سڕینەوەی ئەم عاملە؟")) {
    data2.splice(index, 1);
    saveDataToStorage();
    renderTable2();
    renderTable6();
    updateReports();
  }
}

function startNewMonth() {
  let newMonthName = prompt("ناوی مانگی نوێ بنووسە (بۆ نموونە: مانگی 9):");
  if(!newMonthName) return;
  let currentWorkers = [...new Set(data2.map(w => w.name))];
  if(currentWorkers.length === 0) {
    alert("هیچ عاملێک نییە بۆ گواستنەوە بۆ مانگی نوێ!");
    return;
  }
  currentWorkers.forEach(name => {
    let daysObj = {};
    for(let i=1; i<=31; i++) daysObj[i] = 'present';
    data2.push({ name: name, month: newMonthName, days: daysObj });
  });
  document.getElementById('filterMonthSelect').value = newMonthName;
  saveDataToStorage();
  updateMonthDropdown();
  renderTable2();
  renderTable6();
  alert("مانگی نوێ بە سەرکەوتوویی دەستی پێکرد!");
}

function exportMonthExcel() {
  let currentMonth = document.getElementById('filterMonthSelect').value;
  let filtered = data2.filter(w => w.month === currentMonth);
  if(filtered.length === 0) return alert("هیچ داتایەک نییە بۆ ئەم مانگە!");
  
  let csvContent = "data:text/csv;charset=utf-8,ناوی عامل,مانگ,کۆی غەیاب,کۆی مۆڵەت\n";
  filtered.forEach(w => {
    let abs = 0, lea = 0;
    for(let i=1; i<=31; i++) {
      if(w.days && w.days[i] === 'absent') abs++;
      if(w.days && w.days[i] === 'leave') lea++;
    }
    csvContent += `${w.name},${w.month},${abs},${lea}\n`;
  });
  let encodedUri = encodeURI(csvContent);
  let link = document.createElement("a");
  link.setAttribute("href", encodedUri);
  link.setAttribute("download", `Ghyabat_${currentMonth}.csv`);
  document.body.appendChild(link);
  link.click();
  document.body.removeChild(link);
}

// ================= یوزەرەکان =================
function addNewUser() {
  let u = document.getElementById('newRegUser').value.trim();
  let p = document.getElementById('newRegPass').value.trim();
  let r = document.getElementById('newRegRole').value;
  if(!u || !p) return alert("تکایە ناوی بەکارهێنەر و تێپەڕەوشە بنووسە!");
  
  usersList.push({ username: u, password: p, role: r });
  saveDataToStorage();
  document.getElementById('newRegUser').value = '';
  document.getElementById('newRegPass').value = '';
  renderUsersTable();
  alert("یوزەری نوێ زیادکرا!");
}

function renderUsersTable() {
  let tbody = document.getElementById('usersTableBody');
  if(!tbody) return;
  tbody.innerHTML = '';
  usersList.forEach((user, index) => {
    tbody.innerHTML += `<tr class="hover:bg-zinc-800/50 transition">
      <td class="border-b border-zinc-800 px-3 py-3 font-bold text-white">${user.username}</td>
      <td class="border-b border-zinc-800 px-3 py-3">${user.password}</td>
      <td class="border-b border-zinc-800 px-3 py-3">${user.role === 'admin' ? 'ادمین' : 'مۆبایلی مختبر'}</td>
      <td class="border-b border-zinc-800 px-3 py-3">${user.username !== 'admin' ? `<button onclick="deleteUser(${index})" class="text-rose-400 hover:text-rose-300 font-bold">🗑️</button>` : '-'}</td>
    </tr>`;
  });
}

function deleteUser(index) {
  if(confirm("دڵنیایت لە سڕینەوەی ئەم یوزەرە؟")) {
    usersList.splice(index, 1);
    saveDataToStorage();
    renderUsersTable();
  }
}

// ================= مامەڵەکان (کڕین و فرۆشتن و قەرز) =================
function saveTransaction() {
  let cName = document.getElementById('tCustomerName').value.trim();
  let iType = document.getElementById('tItemType').value;
  let tType = document.getElementById('tType').value;
  let pType = document.getElementById('tPaymentType').value;
  let qty = parseFloat(document.getElementById('tQuantity').value) || 0;
  let unit = document.getElementById('tUnit').value;
  let currency = document.getElementById('tCurrency').value;
  let unitPrice = parseFloat(document.getElementById('tUnitPrice').value) || 0;

  if(!cName || qty <= 0 || unitPrice <= 0) return alert("تکایە خانەکان بە دروستی پڕبکەرەوە!");

  let total = qty * unitPrice;
  let now = new Date().toLocaleDateString();

  data5.push({ cName, iType, tType, pType, qty, unit, currency, unitPrice, total, date: now });
  saveDataToStorage();

  document.getElementById('tCustomerName').value = '';
  document.getElementById('tQuantity').value = '';
  document.getElementById('tUnitPrice').value = '';
  renderTable5();
  updateReports();
}

function renderTable5() {
  let tbody = document.getElementById('tableBody5');
  if(!tbody) return;
  tbody.innerHTML = '';
  
  let totalDebtIQD = 0;
  let totalDebtUSD = 0;
  let totalCashSum = 0;

  data5.forEach((item, index) => {
    if(item.pType === 'قەرز') {
      if(item.currency === 'IQD') totalDebtIQD += item.total;
      else totalDebtUSD += item.total;
    } else {
      totalCashSum += item.total;
    }

    let pTypeBadge = item.pType === 'قەرز' ? '<span class="bg-indigo-500/10 text-indigo-400 px-2 py-0.5 rounded-md border border-indigo-500/20">قەرز</span>' : '<span class="bg-amber-500/10 text-amber-400 px-2 py-0.5 rounded-md border border-amber-500/20">حازر</span>';

    tbody.innerHTML += `<tr class="hover:bg-zinc-800/50 transition">
      <td class="border-b border-zinc-800 px-3 py-3">${index + 1}</td>
      <td class="border-b border-zinc-800 px-3 py-3 font-bold text-white">${item.cName}</td>
      <td class="border-b border-zinc-800 px-3 py-3">${item.iType}</td>
      <td class="border-b border-zinc-800 px-3 py-3 font-bold ${item.tType === 'فرۆشتن' ? 'text-teal-400' : 'text-amber-400'}">${item.tType}</td>
      <td class="border-b border-zinc-800 px-3 py-3">${item.qty} ${item.unit}</td>
      <td class="border-b border-zinc-800 px-3 py-3">${item.unitPrice}</td>
      <td class="border-b border-zinc-800 px-3 py-3 font-extrabold text-white">${item.total.toLocaleString()} ${item.currency}</td>
      <td class="border-b border-zinc-800 px-3 py-3">${pTypeBadge}</td>
      <td class="border-b border-zinc-800 px-3 py-3 text-zinc-400 text-[11px]">${item.date}</td>
      <td class="border-b border-zinc-800 px-3 py-3"><button onclick="deleteTransaction(${index})" class="text-rose-400 hover:text-rose-300 font-bold">🗑️</button></td>
    </tr>`;
  });

  document.getElementById('totalDebtIQD').innerText = totalDebtIQD.toLocaleString() + " دینار";
  document.getElementById('totalDebtUSD').innerText = totalDebtUSD.toLocaleString() + " $";
  document.getElementById('totalCashSum').innerText = totalCashSum.toLocaleString();
}

function deleteTransaction(index) {
  if(confirm("دڵنیایت لە سڕینەوەی ئەم مامەڵەیە؟")) {
    data5.splice(index, 1);
    saveDataToStorage();
    renderTable5();
    updateReports();
  }
}

// ================= مووچە و مسرەف =================
function renderTable6() {
  let workerSelect = document.getElementById('workerSalarySelect');
  let currentMonth = document.getElementById('filterMonthSelect').value;
  if(workerSelect) {
    workerSelect.innerHTML = '';
    let workersInMonth = data2.filter(w => w.month === currentMonth);
    workersInMonth.forEach(w => {
      workerSelect.innerHTML += `<option value="${w.name}">${w.name}</option>`;
    });
  }

  // خشتەی مووچە
  let salaryTbody = document.getElementById('workerSalariesTableBody');
  if(salaryTbody) {
    salaryTbody.innerHTML = '';
    let workersInMonth = data2.filter(w => w.month === currentMonth);
    workersInMonth.forEach(w => {
      let absCount = 0;
      let leaveCount = 0;
      for(let i=1; i<=31; i++) {
        if(w.days && w.days[i] === 'absent') absCount++;
        if(w.days && w.days[i] === 'leave') leaveCount++;
      }

      let key = `${w.name}_${currentMonth}`;
      let setting = workerSalaries[key] || { base: 0, currency: 'IQD' };
      // کەمکردنەوە بۆ هەر غەیابێک (بۆ نموونە ڕۆژێک مووچەی یەک ڕۆژ کەم دەبێتەوە)
      let dailyRate = setting.base / 30;
      let finalSalary = setting.base - (absCount * dailyRate);
      if(finalSalary < 0) finalSalary = 0;

      salaryTbody.innerHTML += `<tr class="hover:bg-zinc-800/50 transition">
        <td class="border-b border-zinc-800 px-3 py-3 font-bold text-white">${w.name}</td>
        <td class="border-b border-zinc-800 px-3 py-3 text-zinc-400">${currentMonth}</td>
        <td class="border-b border-zinc-800 px-3 py-3 font-bold text-rose-400">${absCount} ڕۆژ</td>
        <td class="border-b border-zinc-800 px-3 py-3 font-bold text-amber-400">${leaveCount} ڕۆژ</td>
        <td class="border-b border-zinc-800 px-3 py-3">${setting.base.toLocaleString()} ${setting.currency}</td>
        <td class="border-b border-zinc-800 px-3 py-3 font-black text-teal-400">${finalSalary.toLocaleString(undefined, {maximumFractionDigits: 0})} ${setting.currency}</td>
      </tr>`;
    });
  }

  // خشتەی مسرەفەکان
  let expTbody = document.getElementById('expensesTableBody');
  if(expTbody) {
    expTbody.innerHTML = '';
    expensesList.forEach((ex, index) => {
      expTbody.innerHTML += `<tr class="hover:bg-zinc-800/50 transition">
        <td class="border-b border-zinc-800 px-3 py-3">${index + 1}</td>
        <td class="border-b border-zinc-800 px-3 py-3 font-bold text-white">${ex.title}</td>
        <td class="border-b border-zinc-800 px-3 py-3 font-bold text-amber-400">${ex.amount.toLocaleString()} ${ex.currency}</td>
        <td class="border-b border-zinc-800 px-3 py-3 text-zinc-400 text-[11px]">${ex.date}</td>
        <td class="border-b border-zinc-800 px-3 py-3"><button onclick="deleteExpense(${index})" class="text-rose-400 hover:text-rose-300 font-bold">🗑️</button></td>
      </tr>`;
    });
  }
}

function saveWorkerSalarySetting() {
  let name = document.getElementById('workerSalarySelect').value;
  let base = parseFloat(document.getElementById('workerBaseSalary').value) || 0;
  let currency = document.getElementById('workerSalaryCurrency').value;
  let currentMonth = document.getElementById('filterMonthSelect').value;

  if(!name) return alert("هیچ عاملێک هەڵنەبژێردراوە!");

  let key = `${name}_${currentMonth}`;
  workerSalaries[key] = { base, currency };
  saveDataToStorage();
  renderTable6();
  alert("مووچەی عامل پاشەکەوتکرا!");
}

function saveExpense() {
  let title = document.getElementById('expenseTitle').value.trim();
  let amount = parseFloat(document.getElementById('expenseAmount').value) || 0;
  let currency = document.getElementById('expenseCurrency').value;

  if(!title || amount <= 0) return alert("تکایە ناوی مسرەف و بڕەکەی بنووسە!");

  let date = new Date().toLocaleDateString();
  expensesList.push({ title, amount, currency, date });
  saveDataToStorage();

  document.getElementById('expenseTitle').value = '';
  document.getElementById('expenseAmount').value = '';
  renderTable6();
  updateReports();
}

function deleteExpense(index) {
  if(confirm("دڵنیایت لە سڕینەوەی ئەم مسرەفە؟")) {
    expensesList.splice(index, 1);
    saveDataToStorage();
    renderTable6();
    updateReports();
  }
}

// ================= ڕاپۆرتی گشتی =================
function updateReports() {
  let totalSales = data5.filter(t => t.tType === 'فرۆشتن' && t.pType === 'حازر').reduce((sum, t) => sum + t.total, 0);
  let totalExpenses = expensesList.reduce((sum, e) => sum + e.amount, 0);
  let netProfit = totalSales - totalExpenses;

  document.getElementById('reportTotalSales').innerText = totalSales.toLocaleString();
  document.getElementById('reportTotalExpenses').innerText = totalExpenses.toLocaleString();
  document.getElementById('reportNetProfit').innerText = netProfit.toLocaleString();

  let profitCardBg = document.getElementById('profitCardBg');
  let profitTitle = document.getElementById('profitTitle');
  if(netProfit < 0) {
    profitCardBg.className = "bg-rose-500/10 p-5 rounded-2xl border border-rose-500/20";
    profitTitle.innerText = "زیان (خسار)";
  } else {
    profitCardBg.className = "bg-emerald-500/10 p-5 rounded-2xl border border-emerald-500/20";
    profitTitle.innerText = "پوختە (قازانج / فایدە)";
  }

  let uniqueWorkers = [...new Set(data2.map(w => w.name))];
  document.getElementById('reportWorkersCount').innerText = uniqueWorkers.length + " عامل";
  document.getElementById('reportFahsCount').innerText = data1.length + " فحص";
  document.getElementById('reportMaterialsCount').innerText = data1.length + " مواد";
  document.getElementById('reportTransCount').innerText = data5.length + " مامەڵە";

  let totalDebt = data5.filter(t => t.pType === 'قەرز').reduce((sum, t) => sum + t.total, 0);
  document.getElementById('reportTotalDebt').innerText = totalDebt.toLocaleString();
  document.getElementById('reportPeopleBalance').innerText = (totalSales - totalExpenses).toLocaleString();
}
</script>
</body>
</html>
