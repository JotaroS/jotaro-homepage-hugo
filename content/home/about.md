+++
# About/Biography widget.

date = "2016-04-20T00:00:00"
draft = false

widget = "about"

# Order that this section will appear in.
weight = 1

# List your academic interests.
[interests]
  interests = [
    "Virtual Reality",
    "Human Interface",
    "Human Computer Interaction",
    "Haptic Device and Haptics Design",
    "Hacking 3D Printer for Novel Use"
  ]

# List your Awards and honors if any

[[honors.awards]]
  name = "CHI2019 Best Paper Honorable Mention"
  description = "Project Transcalibur"
  year = 2019

[[honors.awards]]
  name = "Fellowship of Funai Foundation of Information Technology"
  description = "Scholarship of 2500USD / month"
  year = 2019

[[honors.awards]]
  name = "HATAKEYAMA award"
  description = "Japan Society of Mechanical Engineering, the Best Student Award"
  year = 2014

# List your qualifications (such as academic degrees).

[[education.courses]]
  course = "PhD candidate at HCI group in Hasso Plattner Institute"
  institution = "Hasso Plattner Institute, with Prof. Patrick Baudisch"
  year = 2018

[[education.courses]]
  course = "Master's student in Cyber Interface Lab"
  institution = "The University of Tokyo with Prof. Michitaka Hirose"
  year = 2017

[[education.courses]]
  course = "BSc in Mechano-Informatics"
  institution = "The University of Tokyo, Faculty of Engineering (2014-2017), with Prof. Michitaka Hirose"
  year = 2017

[[education.courses]]
  course = "A.Sc in Mechanical and Electrical Engineering"
  institution = "Tokuyama National College of Technology, The top on the list (2009-2014), with Prof. Kurt Fischer"
  year = 2014




+++ 
<!-- Your profile description here... -->
<p id='language_display'>
Jotaro Shigeyama (born in 1993) is currently a Master's student at Hasso Plattner Institute in University of Potsdam / Cyber Interface Lab, the University of Tokyo. He is also a Ph.D candidate in Hasso Plattner Institute in University of Potsdam, with Prof. Patrick Baudisch. 
He is a fellow student of Funai Fountation for Information Technology since 2019.
He is studying computer science in the graduate school of The University of Tokyo, after finished Associate degree in mechanical and electrical engineering in Tokuyama college of technology and Bachelor's degree in mechano-informatics engineering in the University of Tokyo with Prof. Michitaka Hirose.
He received _HATAKEYAMA_ award for his academic excellency in mechanical engineering.
His project was presented in various top-tier international conference including _ACM SIGGRAPH / CHI / UIST.
His current research area is haptics, virtual reality and human computer interaction.
</p>


<script type="text/javascript">

		window.onload = function() {
		display();
	}

	let language_flg = 1;
	function display() {
		if(language_flg == 0) {
            document.getElementById("language_display").innerHTML = "<p id='japanese'>茂山丈太郎：山口県下松市出身．徳山工業高等専門学校 機械電気工学科，東京大学工学部 機械情報工学科，東京大学大学院 学際情報学府を経て，現在ドイツ・Hasso Plattner Institute Human Computer Interaction LabにてPh.D課程に在学中．主な受賞歴として，2019年度船井情報科学振興財団奨学生，ACM CHI2019 Best Paper Honorable Mention Awardや日本機械学会 畠山賞など．現在はVR・アクセシビリティのための触覚デバイスや，機械工学の領域を応用したデジタルファブリケーションシステムの研究開発に取り組む．</p>";
		} else {
            document.getElementById("language_display").innerHTML = "Jotaro Shigeyama (born in 1993) is currently a Master student at Hasso Plattner Institute in University of Potsdam / Cyber Interface Lab, the University of Tokyo. He is also a Ph.D candidate in Hasso Plattner Institute in University of Potsdam, with Prof. Patrick Baudisch. He is a fellow student of Funai Fountation for Information Technology since 2019.He is studying computer science in the graduate school of The University of Tokyo, after finished Associate degree in mechanical and electrical engineering in Tokuyama college of technology and Bachelor degree in mechano-informatics engineering in the University of Tokyo with Prof. Michitaka Hirose. He received HATAKEYAMA award for his academic excellency in mechanical engineering. His project was presented in various top-tier international conference including ACM SIGGRAPH / CHI / UIST. His current research area is haptics, virtual reality and human computer interaction.";
		}
	}

	function language_change() {
		if(language_flg == 0) {
			language_flg = 1;
		} else {
			language_flg = 0;
		}
		display();
	}

</script>