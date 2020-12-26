clear all ; close all ; clc ;
imgrgb = imread("para.jpeg");
figure,imshow(imgrgb),title("Orjinal Görüntü");
[merkezler , yaricaplar] = imfindcircles(imgrgb,[60 110],'ObjectPolarity','bright','Sensitivity',0.97,'Method','TwoStage');
imshow(imgrgb);
viscircles(merkezler,yaricaplar);
toplam = 0;
Xmerkez = [merkezler(:,1)];
Ymerkez = [merkezler(:,2)];
for i=1:length(yaricaplar)
   if yaricaplar(i) > 100
       toplam = toplam + 1;
       text(Xmerkez(i)-25,Ymerkez(i),'1 TL','FontSize',15,'FontWeight','bold','Color','b');
   elseif yaricaplar(i) > 90
       toplam = toplam +0.50;
       text(Xmerkez(i)-35,Ymerkez(i),'0.5 TL','FontSize',15,'FontWeight','bold','Color','b');
   elseif yaricaplar(i) > 75
       toplam = toplam +0.25;
       text(Xmerkez(i)-55,Ymerkez(i),'0.25 TL','FontSize',15,'FontWeight','bold','Color','b');
   else
       toplam = toplam +0.05;
       text(Xmerkez(i)-60,Ymerkez(i),'0.05 TL','FontSize',15,'FontWeight','bold','Color','b');
   end
  
    
end

yazilan = sprintf("%.2f",toplam);
text(1100 , 850,['Toplam = ',yazilan,'TL'],'Color','g','FontSize',14,'FontWeight','bold');
