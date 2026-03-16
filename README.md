TXx_CONUS_plots_evgam_extremes_1940-2025 : it's really just a first look comparing evgam and extRemes results. 


TXx_USA_plots_extremes_1940vs1979.ipynb : Compare extRemes analyses at each point using a time covariate on the location and scale parameters for the 1941-2025 period versus the 1979-2025 period.   

TXx_USA_plots_extremes_PDO_1979.ipynb : Compare extRemes analyses at each point using a time covariate (GLOST) on the location and scale parameters and also a (June-July-August) PDO covariate on the location parameter for the 1941-2025 period versus the 1979-2025 period. 

P value computation:

    %R m_gev <- fevd(TXx, data = r_df,type='GEV')
    %R m_gevL <- fevd(TXx, data = r_df, type='GEV', location.fun= ~ glost )
    %R m_gevLS <- fevd(TXx, data = r_df, type='GEV',location.fun= ~ glost, scale.fun= ~ glost )
    %R m_gevLLpS <- fevd(TXx, data = r_df, type='GEV',location.fun= ~ glost + PDO, scale.fun= ~ glost )

    %R rpvalueL <- lr.test(m_gev, m_gevL)$p.value        # Location - GLOST smooth
    %R rpvalueLp <- lr.test(m_gevLS, m_gevLLpS)$p.value  # Location - PDO smooth
    %R rpvalueS <- lr.test(m_gevL, m_gevLS)$p.value      # Scale - GLOST smooth



TXx_USA_plots_extremes_PDO_1979_pvalue1.ipynb : Compare extRemes analyses at each point using a time covariate (GLOST) on the location and scale parameters and also a (June-July-August) PDO covariate on the location parameter for the 1941-2025 period versus the 1979-2025 period. 

P value computation:

    %R m_gev <- fevd(TXx, data = r_df,type='GEV')
    %R m_gevL <- fevd(TXx, data = r_df,type='GEV', location.fun= ~ glost )
    %R m_gevS <- fevd(TXx, data = r_df,type='GEV', scale.fun= ~ glost )
    %R m_gevLLpS <- fevd(TXx, data = r_df,type='GEV',location.fun= ~ PDO )

    %R rpvalueL <- lr.test(m_gev, m_gevL)$p.value      # Location - GLOST smooth
    %R rpvalueLp <- lr.test(m_gev, m_gevLp)$p.value    # Location - PDO smooth
    %R rpvalueS <- lr.test(m_gev, m_gevS)$p.value      # Scale - GLOST smooth
