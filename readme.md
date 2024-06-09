```math
\newcount\iii
\newdimen\tempx
\newdimen\tempy
\newdimen\Slope
\newdimen\temp
\newdimen\temptwo
\newdimen\tempthree
\newdimen\tempfour
\newdimen\cinc
\newdimen\x
\setbox46\hbox{{\kern-.1pt\vrule width.6 pt height .4pt depth0pt}}
\setbox48\hbox{{\kern-.1pt\vrule width.6 pt height .4pt depth0pt}}
    %
    %    Sketch the graph of r=#1(#2+#3 cos(#4 \theta) from theta = #5 to #6.  #7 controls the resolution (higher for finer resolution) )
    %    The produced size will be r_max=#1*(#2+#3) points.  Arguments are numbers (no ''pt'')
    %
    \newdimen\ct\newdimen\st
    \def\CosPolarGraph#1#2#3#4#5#6#7{% 
          \x=#5 pt  
                \temptwo=#7pt \ifdim\temptwo<0 pt \temptwo=-\temptwo\fi \cinc=.01pt \DivDim\cinc\temptwo\to\cinc 
                \temp=#4pt 
                \tempthree=#3 pt
          \loop\ifdim\x<#6pt%
                     {\Cos{\x}\to\ct 
                        \Sin{\x}\to\st  
                        \MulDim\temp\x\to\tempfour              %
                        \Cos\tempfour\to\tempfour               %   compute r
                        \MulDim\tempfour\tempthree\to\tempfour  %
                        \tempthree=#1 pt                        % 
                        \advance\tempfour by #2 pt              % 
                        \MulDim\tempfour\tempthree\to\tempfour  %
                        \MulDim\st\tempfour\to\tempy
                        \MulDim\ct\tempfour\to\tempx
                        \GRLABEL{\copy46}(\tempx,\tempy)}%
                      \advance\x by \cinc
           \repeat} 
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    %
    %
    %    Sketch the graph of r=#1(#2+#3 sin(#4 \theta) from #5 to #6.  #7 controls the resolution (higher for finer resolution) )
    %    The produced size will be r_max=#1*(#2+#3) points.  Arguments are numbers (no ''pt'')
    %                                                                       
    \def\SinPolarGraph#1#2#3#4#5#6#7{%  
          \x=#5 pt  
                \temp=#7pt \ifdim\temp<0 pt \temp=-\temp\fi \cinc=.01pt \DivDim\cinc\temp\to\cinc 
                \loop\ifdim\x<#6pt%
                     {\temp=#4pt
                      \MulDim\temp\x\to\tempfour              %
                        \Sin\tempfour\to\tempfour               % 
                        \temp=#3 pt                             %   compute r
                        \MulDim\tempfour\temp\to\tempfour       %
                        \temp=#1 pt                             % 
                        \advance\tempfour by #2 pt              % 
                        \MulDim\tempfour\temp\to\tempfour       %%%%%
                        \Sin{\x}\to\temp
                        \MulDim\temp\tempfour\to\tempy           
                        \Cos{\x}\to\temp                            
                        \MulDim\temp\tempfour\to\tempx           
                        \GRLABEL{\copy46}(\tempx,\tempy)}%
                      \advance\x by \cinc
           \repeat}     
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    %
    % Archimedian Spiral. Sketch the graph of r=#1 * \theta from #2 to #3  
    %
    %                           
    \def\Spiral#1#2#3{% 
          \x=#2 pt% 
                \cinc=.01pt%  
                \loop\ifdim\x<#3pt%
                     \temp=#1pt
                      \MulDim\temp\x\to\tempfour                   % Compute r
                        {\Sin{\x}\to\temp
                        \MulDim\temp\tempfour\to\tempy                
                        \Cos{\x}\to\temp                            
                        \MulDim\temp\tempfour\to\tempx                
                        \GRLABEL{\copy46}(\tempx,\tempy)}%
                      \advance\x by \cinc
           \repeat}                                                                                 
    %%%%%%%%%%%%        
```