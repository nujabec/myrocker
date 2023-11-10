# https://github.com/rocker-org/rocker-versioned2
FROM rocker/geospatial:4.3.2

# OS環境（rockerはdebianベース）に日本語ロケールを追加し切り替え
ENV LANG ja_JP.UTF-8
ENV LC_ALL ja_JP.UTF-8

# 日本語化
RUN sed -i '$d' /etc/locale.gen && \  
    echo "ja_JP.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen ja_JP.UTF-8 && \
    /usr/sbin/update-locale LANG=ja_JP.UTF-8 LANGUAGE="ja_JP:ja" && \
    /bin/bash -c "source /etc/default/locale" && \
    ln -sf  /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    apt-get update && apt-get install -y fonts-ipaexfont fonts-noto-cjk && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

#  Rパッケージをimport
RUN R -e "options(repos = c(CRAN = 'https://cran.ism.ac.jp/'))" && \
    install2.r --error --skipinstalled --deps TRUE --ncpu -1 \
    here && \
    # tidylog \
    # DBI \
    # RPostgreSQL \
    # odbc \
    # pacman \
    # rio \
    # openxlsx \
    # renv \
    # remotes \
    # linelist \
    # naniar \
    # janitor \
    # gtsummary \
    # rstatix \
    # broom \
    # lmtest \
    # easystats \
    # parameters \
    # see \
    # cowplot \
    # patchwork \
    # RColorBrewer \
    # ggnewscale \
    # ggridges \
    # DiagrammeR \
    # ggrepel \
    # plotly \
    # gganimate \
    # sf \
    # tmap \
    # OpenStreetMap \
    # spdep \
    # rmarkdown \
    # reportfactory \
    # flexdashboard \
    # shiny \
    # knitr \
    # DT \
    # gt \
    # huxtable \
    # gsDesign \
    # shinydashboard \
    # formattable \
    # ggplotgui \
    # ggraptR \
    # MASS \
    # rJava \
    # pool \
    # Rmisc \
    # celestial \
    # NipponMap \
    # GGally \
    # ggmap \
    # ggmosaic \
    # Hmisc \
    # kableExtra \
    # mice \
    # summarytools \
    # zipangu \
    # coin \
    # sessioninfo \
    # styler \
    # sqldf \
    # Matching \
    # MatchIt \
    # WeightIt \
    # epiR \
    # cobalt \
    # glmnet \
    # glmnetUtils \
    # rpart \
    # partykit \
    # pROC \
    # caret \
    # Amelia \
    # tibbletime \
    # xts \
    # forecast \
    # rstan \
    # styler \
    # survival \
    # survminer \
    # broom \
    # lme4 \
    # lmerTest \
    # gee \
    # geepack \
    # emmeans \
    # interactions \
    # forestplot \
    # boot \
    # logistf \
    # ggsci \
    # ggfortify \
    # ggbeeswarm \
    # ggpubr \
    # lubridate \
    # haven \
    # esquisse \
    # tableone \
    # RMySQL \
    # jsonlite \
    # checkpoint \
    # emmeans \
    # curl \
    # doParallel \
    # reshape2 \
    # qlcMatrix \
    # proxy \
    # moments \
    # greybox \
    # muhaz \
    # rpart.plot \
    # ranger \
    # xgboost \
    # tm \
    # SnowballC \
    # text2vec \
    # kernlab \
    # rpivotTable \
    # DataExplorer \
    # skimr \
    # XLConnect \
    # mlr \
    # terra \
    # spData \
    # mapview \
    # osrm \
    # movecost \
    # miniCRAN \
    # rjson \
    # gghighlight \
    # ggThemeAssist \
    # targets \
    # revealjs \
    # docxtractr \
    # cronR \
    # export \
    # ragg \
    # svglite \
    # fpCompare \
    # devEMF && \
    # # GitHubからRパッケージをinstall
    # installGithub.r \
    # davidgohel/gdtools \
    # davidgohel/officer \
    # davidgohel/flextable \
    # uribo/jpmesh \
    # uribo/jpndistrict \
    # mlr-org/shinyMlr && \
    # インストール時にダウンロードした一時ファイルの削除
    rm -rf /tmp/downloaded_packages/ /tmp/*.rds && \
    echo "copilot-enabled=1" >> /etc/rstudio/rsession.conf && \
    cd /home/rstudio && mkdir .cache .cache/R .cache/R/renv .TinyTeX && \
    chown -R rstudio:rstudio /home/rstudio && \
    chmod -R 777 /home/rstudio

# 設定ファイルのcopy
COPY --chown=rstudio:rstudio rstudio-prefs_mysettings.json /home/rstudio/.config/rstudio/rstudio-prefs.json

# Rプロファイルをコピー - RStudio起動時に実行したいRスクリプトをこのファイルに書くことが出来る
# RStudioのみ再起動した場合も読み込まれます
COPY --chown=rstudio:rstudio dotRprofile /home/rstudio/.Rprofile

# shiny serverのインストール
# RUN  /rocker_scripts/install_shiny_server.sh 

